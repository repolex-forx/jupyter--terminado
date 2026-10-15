# Repolex Knowledge Graph of jupyter/terminado

RDF knowledge graph data for [jupyter/terminado](https://github.com/jupyter/terminado), parsed by [repolex](https://repolex.ai).

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
rlex download jupyter/terminado
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 23a0bf771107fb01ddffdf342b1d5348ad6c702d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 23a0bf771107fb01ddffdf342b1d5348ad6c702d
│           └── chunk-001.nq.gz
├── blob
│   ├── 072980c84c2abde5d8ab412a4e9f17fb57630e33.nq.gz
│   ├── 072f83b78e0213e9703b4dc42e08c4bf09be34a6.nq.gz
│   ├── 079d620943ba07e34334d97a85679f81121d3cbc.nq.gz
│   ├── 0d7b33d8b042235f31f47ec79ae494e30fd30a7a.nq.gz
│   ├── 196c8388a30439df2078deac99c60cd0a493711c.nq.gz
│   ├── 1a169f5994e7009fd7ef9f05e88c31aae2134cba.nq.gz
│   ├── 1d0fca91038feb8461a59756de303aadeb59a1f4.nq.gz
│   ├── 25a6922cefd650e4166e6d2ba6b92dbd7b486d14.nq.gz
│   ├── 396330bb9729d2ec595617aef79fb28600d86bd7.nq.gz
│   ├── 49c6706947e049dc515acbc553f24ee4f19b07d5.nq.gz
│   ├── 4a3146167f2bf443a6ffdbdd5f0ee4a3d72c5e5a.nq.gz
│   ├── 4a988fcab00c149360661cc3ed6fead08fd549a9.nq.gz
│   ├── 511d33d742b06a9c7256434a16004fc2e9440c3b.nq.gz
│   ├── 5295e776b63d7adfab3ddad99962cc6f81968909.nq.gz
│   ├── 5766d3ba0b46ec11f30ca924268877e6b0cae635.nq.gz
│   ├── 5d78f49596ac4842b7b4963c420331a5ec16544f.nq.gz
│   ├── 60af4c5f16741c7c2fe17cdd9718ae5f6d56d8a4.nq.gz
│   ├── 6d208186a868080f061af8f20ab1a008022137c3.nq.gz
│   ├── 70b8f79b2827c79e66ca442002c5eaccd0f7e40c.nq.gz
│   ├── 71364aec8a09eefd22165bfdfb0d0f64f2447967.nq.gz
│   ├── 725feab5ce652dc39f3f2c77b9fd3c90bf049c65.nq.gz
│   ├── 7b4495e3c20b45101d9ff548ae82d29fcc6c46ee.nq.gz
│   ├── 82b65d7a90f4bf70bf9388c6c3d1bd92955981e2.nq.gz
│   ├── 8ecdfae33468e633a8daa247d32d153e51d80d16.nq.gz
│   ├── 929cd3cc19cd9b621819971fc660254137ddcdcb.nq.gz
│   ├── 99e61f260c5a64f7222bf2c7fb64938ce70aa143.nq.gz
│   ├── 99fcdd396ecf9acaa429429aed7044218c1ed165.nq.gz
│   ├── ae81d65fa15c264313c0bcb78bb4368268ef5387.nq.gz
│   ├── aedb3c5fbb89b8e4fcb16d121a7399159915a869.nq.gz
│   ├── b5a7b367cbf2a30834da92c3c1e0d896742abd5c.nq.gz
│   ├── d20ef59d9a011e034bc6f2b8c618db93df508ad8.nq.gz
│   ├── da832b4d0ff8e075dabba1266d71268446573e22.nq.gz
│   ├── dfcd7ee78377b9e3e7e10930505cb8ec1ce75d45.nq.gz
│   ├── e26e441e41b0380c82d5eaeca44d5f99ae929844.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f1de94c3ed786ccf3ae91ee05e343e35cae1defc.nq.gz
│   ├── f23ae3508f3e99ff659eb1d7326bc0ad828b795e.nq.gz
│   └── fcdd3e88b66ec9b10362685146ef2a36088e54f3.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 23a0bf771107fb01ddffdf342b1d5348ad6c702d.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 46 files
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

[jupyter/terminado](https://github.com/jupyter/terminado)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
