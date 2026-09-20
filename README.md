# Engineering under heavy constraints

Private hands-on work, built out in the open: **self-hosted AI, OCR, mesh
networking, and systems debugging — on hardware that fights back.**

No GPU. No public IP. No open ports. An aging home-lab server and a laptop that
together somehow run more software than most cloud accounts care to admit —
all offline-first, all reachable only over a private WireGuard mesh.

```
wasm / docker / wireguard / tailscale / ollama (cpu) / chroma / qdrant / caddy
```

## What I build

- **[htr-consensus-pipeline](https://github.com/vonninnyhammer/htr-consensus-pipeline)** — three independent OCR engines run in parallel; only tokens a majority agree on are trusted. Everything else escalates to a bigger model on a second machine. Tuned for a 4 GB VRAM laptop GPU.
- **[rlm-htr-harness](https://github.com/vonninnyhammer/rlm-htr-harness)** — Recursive-Language-Model scaffold that corrects OCR documents the way humans do: entire document in a REPL, decomposed into per-page sub-calls, cross-referencing names and dates so pages agree with each other.
- **[mempalace-openviking-bridge](https://github.com/vonninnyhammer/mempalace-openviking-bridge)** — a dual-layer, local-first memory: spatial memory (ChromaDB) plus an execution-time RAG filesystem (`viking://`) with L0/L1/L2 tiers. Zero cloud telemetry, verified by an integration test.
- **[wireguard-edge-mesh](https://github.com/vonninnyhammer/wireguard-edge-mesh)** — the hub-and-spoke mesh that ties the hacks together: split-tunnel by design, because the full-tunnel variant once killed every network on the laptop.
- **[constrained-hardware-field-notes](https://github.com/vonninnyhammer/constrained-hardware-field-notes)** — the troubleshooting log: AVX2-less Xeon bricking native wheels, CPU-only LLM inference, CGNAT, broken IPv6 pull failures, and the rest.

## Why "constrained"

The interesting problems aren't the ones you can throw money at. I run LLMs on
CPUs because there's no GPU present. I picked a vector store because the old
Xeon can't execute one instruction. I have no inbound ports, so everything
departs instead. Every one of those constraints made the system better — and
this profile is the paper trail of how.

```
cpu-only inference   ·   quantized models   ·   no inbound ports   ·
pre-cgNAT networking ·   consensus over brute force   ·   debuggable everything
```

## Also

- Field notes and write-ups: **[guison.net](https://guison.net)**
- This is hobby work — nothing here is monetized, most of it started because
  "I wish this existed," and all of it comes with honest footnotes about what
  broke.