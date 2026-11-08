# Repolex Knowledge Graph of bentoml/LLMGateway

RDF knowledge graph data for [bentoml/LLMGateway](https://github.com/bentoml/LLMGateway), parsed by [repolex](https://repolex.ai).

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
rlex download bentoml/LLMGateway
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── c4537e75744959181dcb74fc07c54bf732c0edfd
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── c4537e75744959181dcb74fc07c54bf732c0edfd
│           └── chunk-001.nq.gz
├── blob
│   ├── 82f927558a3dff0ea8c20858856e70779fd02c93.nq.gz
│   ├── ca0be71c0718e59857e844cfb36e603e7e84eb2b.nq.gz
│   ├── cbfd6a68c8b2673cc22d26fe29c9c5d576f2e1d1.nq.gz
│   ├── d61b89c4d4b2ee90dbc9935c7f525cfbee165610.nq.gz
│   ├── d9cf1150b84cca06b20e7dcae3a5941ad67e1d87.nq.gz
│   ├── f36a0c393203a67981902070139f5764a367dbf0.nq.gz
│   └── fc2a564f83a59fdf93a6346ffb395d390081ce43.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── c4537e75744959181dcb74fc07c54bf732c0edfd.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 14 files
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

[bentoml/LLMGateway](https://github.com/bentoml/LLMGateway)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
