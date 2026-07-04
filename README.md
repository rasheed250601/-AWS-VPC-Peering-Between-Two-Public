# 🔗 AWS VPC Peering — Two Public VPCs Connected Securely

A hands-on AWS networking project demonstrating how to establish a **VPC Peering Connection** 
between two isolated VPCs, configure routing on both sides, and verify cross-VPC 
connectivity — all without using the public internet.

---

## 🏗️ Architecture Overview

- **VPC 1** (`my-peer-public1` — `10.1.0.0/16`) — Requester VPC with Internet Gateway
- **VPC 2** (`my-peer-public2` — `10.2.0.0/16`) — Accepter VPC, no Internet Gateway
- **Peering Connection** routes traffic between both VPCs internally via AWS backbone

---

## ✅ What Was Built

| Step | Action |
|------|--------|
| 1 | Created 2 custom VPCs with non-overlapping CIDRs |
| 2 | Created public subnets in each VPC |
| 3 | Established VPC Peering Connection (Active) |
| 4 | Updated Route Tables on both VPCs |
| 5 | Configured Security Groups per VPC |
| 6 | Launched 2 EC2 instances (t2.micro) |
| 7 | Allocated & attached Elastic IP to Server 1 |
| 8 | Connected via EC2 Instance Connect |
| 9 | Verified connectivity with live ping test ✅ |

---

## 🖥️ EC2 Details

| Instance | Private IP | Public IP |
|----------|-----------|-----------|
| my public server 1 (VPC1) | 10.1.1.155 | 52.49.48.249 (Elastic IP) |
| my public server 2 (VPC2) | 10.2.2.128 | None |

---

## 🏓 Ping Test Result

```bash
ping 10.2.2.128
# From Server 1 → Server 2 (cross-VPC)
# Reply: TTL=127, time ~0.8–2.6 ms ✅
