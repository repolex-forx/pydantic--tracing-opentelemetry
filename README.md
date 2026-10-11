# Repolex Knowledge Graph of pydantic/tracing-opentelemetry

RDF knowledge graph data for [pydantic/tracing-opentelemetry](https://github.com/pydantic/tracing-opentelemetry), parsed by [repolex](https://repolex.ai).

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
rlex download pydantic/tracing-opentelemetry
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 13f7ca2c0ad0c2e73a1a4bc6fe1765b83d9c3933
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 13f7ca2c0ad0c2e73a1a4bc6fe1765b83d9c3933
│           └── chunk-001.nq.gz
├── blob
│   ├── 0648ceb017ed2ed22305f792019dbc7009b51df9.nq.gz
│   ├── 1171ac874e45f901c62bdc485b4d05b8717d9a75.nq.gz
│   ├── 131cfb4e79bd7d29ab4efcb188a1d70384e4c530.nq.gz
│   ├── 15949e9cac0c9b44617f01d6e9bac3ae9914a17e.nq.gz
│   ├── 16e41120d6efa6fa2d3b8f0d922df43685122f8e.nq.gz
│   ├── 1b25c837caf01f73716a458c6ab5e3040198ba07.nq.gz
│   ├── 297b0c2274be1c22670e047fdcd5834bd708a40b.nq.gz
│   ├── 2d5e71b3e9be0ea957d8ecbf65cae05b8c5cb33e.nq.gz
│   ├── 2f0520f7e012b4c57a3c88b9f09b1190c95d5d66.nq.gz
│   ├── 32260ead57b1c470b6c576d043722e6bf2690c2b.nq.gz
│   ├── 4cb98d135830218144b8e6575a41233d344a00e1.nq.gz
│   ├── 5f3dac8df33e3bf031226572eaaf8f2e4b3fc8da.nq.gz
│   ├── 6143c8d5013ad205675389197b0c53e9e7a4eaff.nq.gz
│   ├── 64dd6d918843f4e1421d79996b6d6c85d2f84114.nq.gz
│   ├── 6c344ac074be4cf4ab2f425ea135efc4d0cad2bb.nq.gz
│   ├── 74608726e697ff4edff4de8294217b66de548258.nq.gz
│   ├── 776f4269eecda89af3239818e102c7ae66ac2a01.nq.gz
│   ├── 7a6e442a4e25bc0c2bf35b593aabea141eba8017.nq.gz
│   ├── 887a8949d4bb9c7a7506f7d137486dcc2d63ebdc.nq.gz
│   ├── 92017d9c57f317c06b787c50a234f50d5e0e7b50.nq.gz
│   ├── a520820e285a7cca5ebc49e671ab5e1eb3bbb71f.nq.gz
│   ├── a5edf52f02c7419f8518cfe06622ec59e4414a15.nq.gz
│   ├── a68a4b6fe208564cf79d7d4475aec975850f731c.nq.gz
│   ├── acf75e2700b1d10d7db730f3ad505a054ced0248.nq.gz
│   ├── ae56164dae9b20388e8d73081e992af5032e46c5.nq.gz
│   ├── b3f52f0fff3b3696708482bffbb5836322628cdd.nq.gz
│   ├── b7ef6a16185dcdfa6fa18ee6157965535385d8b1.nq.gz
│   ├── ba83aa2e2dd02ef917a1f7aa06d39455b97bd59c.nq.gz
│   ├── bdb61ab015c18338bf96ed083e3c5171dca812e1.nq.gz
│   ├── ccd30acee6b0a6f2e61708a3747a5943a20c951d.nq.gz
│   ├── cdb28b4b56a4860b3872fa837949cf0db13ecc4c.nq.gz
│   ├── d955372bc56aa99189b8e94f03b008adb1da7cda.nq.gz
│   ├── dbc1f9a19d681a7bb8de9380e7545731cf0972f1.nq.gz
│   ├── ee35316f6a5dd555d03d2821aa1573bcba085afb.nq.gz
│   └── f452702b41744f3efc43a1b4d55a44861509bdcd.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 13f7ca2c0ad0c2e73a1a4bc6fe1765b83d9c3933.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 41 files
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

[pydantic/tracing-opentelemetry](https://github.com/pydantic/tracing-opentelemetry)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
