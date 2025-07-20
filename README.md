# aruba-aws-map

> Living cheat-sheet that maps Aruba Cloud **Compute**, **Storage**, **Network**, **Managed DB**, and **Kubernetes** resources to their nearest AWS equivalents—and vice-versa.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Last Updated](https://img.shields.io/github/last-commit/<your-handle>/aruba-aws-map)](https://github.com/<your-handle>/aruba-aws-map/commits/main)

## Why this repo exists

When I moved staging workloads from AWS → Aruba I couldn’t find an up-to-date, side-by-side comparison of the **actual knobs** (disk IOPS, IAM models, network flavours, K8s add-ons).  
SECA is tackling the same problem for IONOS; this repo fills the gap for **Aruba vs. AWS** and is intentionally **narrow in scope**.

Goals  
- One page per resource type (VM, disk, subnet, bucket, cluster, managed DB).  
- Exact CLI/SDK snippets for both clouds.  
- Open PRs for anything that is missing or changes.  
- No grand abstraction—just the facts.

## Quick start

| Task | Aruba | AWS |
|------|-------|-----|
| Launch 2 vCPU / 4 GB VM | `aruba compute create --flavor medium --image ubuntu-22` | `aws ec2 run-instances --instance-type t3.medium --image-id ami-0abcdef1234567890` |
| Attach encrypted 100 GB disk with 3 000 IOPS | `aruba volume create --size 100 --type SSD-3000 --encrypted` | `aws ec2 create-volume --size 100 --volume-type gp3 --iops 3000 --encrypted` |
| Create private subnet | `aruba network subnet create --vpc my-vpc --cidr 10.0.1.0/24 --private` | `aws ec2 create-subnet --vpc-id vpc-12345 --cidr-block 10.0.1.0/24` |

Jump to the full tables:  
- [Compute](docs/compute.md)  
- [Storage](docs/storage.md)  
- [Network](docs/network.md)  
- [Managed Databases](docs/managed-db.md)  
- [Kubernetes](docs/kubernetes.md)

## Contributing

Found a mismatch? Open an issue or PR.  
Please keep each resource in its own file so diffs stay readable.

## Licence

MIT © 2024 [Your Name](LICENSE)