# Rethinking Last-Mile Routing at Scale

**Near-linear planning on commodity hardware**

This repository contains a technical report describing a practical architecture for large-scale last-mile route optimization.

The core idea: at million-stop scale, vehicle routing stops being only an optimization problem and becomes a systems problem involving partitioning, boundary repair, graph reuse, bounded route-level optimization, and orchestration.

## Paper

📄 **[Download the PDF](https://github.com/vizzito/last-mile-optimizer-paper/releases/download/v1.0.0/last_mile_massive_optimizer_paper_v1.pdf)**

## Main results

Under a shared external measurement protocol based on OSRM and Google Maps, using the public Amazon Last Mile Routing Research Challenge dataset:

- **23.3% less measured distance** relative to the released Amazon baseline routes
- **11.1% fewer routes**
- **17.59% mean depot-level distance reduction**
- **1,000,000 stops processed in ~20 minutes** on commodity hardware

## What this is

This is a systems-oriented technical report about making very large last-mile routing workloads practical.

The architecture combines:

- parallel constraint-aware clustering
- constraint-aware vehicle allocation
- distributed boundary rebalancing
- bounded route-level optimization
- localized graph and distance reuse

## What this is not

This report does **not** claim to reproduce Amazon’s internal routing objective.

The benchmark compares released Amazon route files and generated route files over the same stops using a shared external OSRM/Google measurement protocol. The goal is to compare routing structure under a reproducible external metric, not to infer or match Amazon’s proprietary operational objective.

## Validation

A separate verifier repository is available here:

https://github.com/vizzito/last-mile-route-verifier

It is intended to help inspect and reproduce the external distance comparison protocol.

## Why this matters

Many routing APIs and logistics systems work well at small or moderate request sizes, but require manual pre-partitioning, strict input caps, or large infrastructure for very large workloads.

This report explores an alternative: organizing the routing problem into bounded, composable stages so that workloads from thousands to one million stops can be planned predictably on commodity hardware.

## Citation

```bibtex
@misc{vizzolini2026rethinking,
  author       = {Martin Vizzolini},
  title        = {Rethinking Last-Mile Routing at Scale: Near-Linear Planning on Commodity Hardware},
  year         = {2026},
  howpublished = {Technical report},
  url          = {https://github.com/vizzito/last-mile-optimizer-paper/releases/tag/v1.0.0}
}
