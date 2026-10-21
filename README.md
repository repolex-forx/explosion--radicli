# Repolex Knowledge Graph of explosion/radicli

RDF knowledge graph data for [explosion/radicli](https://github.com/explosion/radicli), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/radicli
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── c472cf80939c0a8a5fde1f958d5af3f903ad195c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── c472cf80939c0a8a5fde1f958d5af3f903ad195c
│           └── chunk-001.nq.gz
├── blob
│   ├── 1b89dd28d855ab560342488ff0fde0bc6ec1189b.nq.gz
│   ├── 22ba14e58e703a33c5d74d17ff501aa8c96cb0fe.nq.gz
│   ├── 2a0ac93f3ae893588ca7e0be94648ce06e6a2e43.nq.gz
│   ├── 36d2679f63c044dffc911124184ee8ba2431dd8d.nq.gz
│   ├── 4285d1792b8cb0c77e2b125d54dfef54f1931035.nq.gz
│   ├── 5cfbd9ac3369094110dc35dd4fe89d0420dbf0ba.nq.gz
│   ├── 5fa1ffd028cc83c6701d730d6c28c05e8db52bab.nq.gz
│   ├── 63562f99680e85f395807cd6dd5bad59bdadf588.nq.gz
│   ├── 784fcc85cb4371269840d6ff096ab652d84784d4.nq.gz
│   ├── 916418f1191710f100a14f4ea8f25d9722932a66.nq.gz
│   ├── 9600d6614f7d0a03057d951b3e6e5c7bde2c70eb.nq.gz
│   ├── a82437566a18ee0e70013e4319fa868f049505ba.nq.gz
│   ├── c3d6b5398c99ac344ab074a377984322e5c15d18.nq.gz
│   ├── c7f63b36d665979ee6ee89799e7ace175939efb8.nq.gz
│   ├── cc48a3ca9db9a1f0aa643223e9d5bcdd1b32fd78.nq.gz
│   ├── d004ba53a1a9a9661a3d917794b8b6733a356033.nq.gz
│   ├── d4c5c3d676281c768fc138e0e7223a74b957586e.nq.gz
│   ├── dc34d8aca8622a24ee9328c86dd248c1a418f431.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f5a4e4397162a0c100d48029c39fce3036661141.nq.gz
│   └── f96d49e9f26f85976875cee617e5bd58229a3e2d.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── c472cf80939c0a8a5fde1f958d5af3f903ad195c.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 29 files
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

[explosion/radicli](https://github.com/explosion/radicli)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
