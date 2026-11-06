# Repolex Knowledge Graph of sphinx-contrib/rawfiles

RDF knowledge graph data for [sphinx-contrib/rawfiles](https://github.com/sphinx-contrib/rawfiles), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download sphinx-contrib/rawfiles
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4289d667234758c6c5530cf85e18fa81f04b9709
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 4289d667234758c6c5530cf85e18fa81f04b9709
│           └── chunk-001.nq.gz
├── blob
│   ├── 2eba9160d403563d8b100534a4d950281de057e6.nq.gz
│   ├── 32f058fda82b7ad232f99b9e475bc369ae02cbf9.nq.gz
│   ├── 368768db0fdb86edb55401dda936dcf32a276a32.nq.gz
│   ├── 3e5c226e60d40818ed6c6c53801d2a854e0251df.nq.gz
│   ├── 8e7e2bc0d26ebc39199523caf9850ff62f3d650a.nq.gz
│   ├── a4591ad8f68dd7f96731a76e965813ec9dffc6c0.nq.gz
│   ├── b5a7dc29ef0f7f3593b1c61cfc5dfe8a17d3918c.nq.gz
│   ├── bfb9f4b5e992f8af7ca8153e93dab5c67e47976f.nq.gz
│   └── eea263f6595c2cb5ff145e51976df69b162c88a9.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 4289d667234758c6c5530cf85e18fa81f04b9709.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 16 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[sphinx-contrib/rawfiles](https://github.com/sphinx-contrib/rawfiles)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
