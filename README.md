# Hilltop Guest House – Redundant Network Design

## Project Overview

This project demonstrates the design and implementation of a redundant enterprise network for Hilltop Guest House using Cisco Packet Tracer.

The network is designed with separate VLANs for Guest, Staff, and Management departments. It uses a redundant core switching architecture, EtherChannel, and Spanning Tree Protocol (STP) to improve network availability and prevent switching loops.

## 1. Network Topology

The network consists of:

- 2 Cisco Routers
- 2 Cisco Catalyst 3560 Multilayer Core Switches
- 2 Cisco Catalyst 2960 Access Switches
- 9 End Devices (PCs)
- Redundant connections between core and access switches
- EtherChannel links between core switches

## 2. VLAN Configuration

| VLAN ID | VLAN Name | Department |
|---|---|---|
| 10 | GUEST | Guest Network |
| 20 | STAFF | Staff Network |
| 30 | MANAGEMENT | Management Network |

## 3. IP Addressing and Gateway Plan

Base Network: `192.168.100.0/24`

| Department | VLAN | Network Address | Subnet Mask | Default Gateway | Usable IP Range | Broadcast |
|---|---:|---|---|---|---|---|
| Guest | 10 | 192.168.100.0/26 | 255.255.255.192 | 192.168.100.1 | 192.168.100.2 – 192.168.100.62 | 192.168.100.63 |
| Staff | 20 | 192.168.100.64/27 | 255.255.255.224 | 192.168.100.68 | 192.168.100.65 – 192.168.100.94 | 192.168.100.95 |
| Management | 30 | 192.168.100.96/28 | 255.255.255.240 | 192.168.100.98 | 192.168.100.97 – 192.168.100.110 | 192.168.100.111 |

## 4. Sample PC IP Configuration

The following IP addresses are visible in the network topology:

| Device | IP Address | Default Gateway | VLAN |
|---|---|---|---|
| PC0 | 192.168.100.2 | 192.168.100.1 | 10 |
| PC3 | 192.168.100.69 | 192.168.100.68 | 20 |
| PC8 | 192.168.100.101 | 192.168.100.98 | 30 |

## 5. Redundant Core Switching Architecture

Two multilayer switches are deployed as the core layer, with two access switches connected redundantly.

Key implementation features:

- Redundant links between core and access switches.
- Multiple paths for network availability.
- EtherChannel between core switches.
- VLAN trunking between switches.
- STP for Layer 2 loop prevention.

## 6. EtherChannel Configuration

LACP EtherChannel is implemented between the two core switches.

| Parameter | Configuration |
|---|---|
| Protocol | LACP |
| Port-Channel | Port-Channel 1 |
| Physical Interfaces | Fa0/3 and Fa0/4 |
| Purpose | Link aggregation and redundancy |

EtherChannel combines multiple physical connections into one logical connection, providing increased link capacity and redundancy.

## 7. Spanning Tree Protocol (STP)

PVST is used to prevent Layer 2 switching loops and manage redundant paths.

### Root Bridge Design

| VLAN | Department | Root Bridge |
|---|---|---|
| 10 | Guest | Core-SW1 |
| 20 | Staff | Core-SW1 |
| 30 | Management | Core-SW2 |

STP allows redundant paths to remain available while preventing forwarding loops.

## 8. Additional Switching Features

- IEEE 802.1Q trunking
- VLAN segmentation
- PortFast configuration
- BPDU Guard configuration
- LACP EtherChannel
- Redundant uplinks
- STP root bridge selection

## 9. Technologies and Tools

- Cisco Packet Tracer
- Cisco IOS
- VLANs
- VLSM Subnetting
- Layer 2 and Layer 3 Switching
- 802.1Q Trunking
- Spanning Tree Protocol (PVST)
- LACP EtherChannel
- Network Redundancy

## 10. Project Files

This repository includes:

- Packet Tracer topology file (.pkt)
- Network topology screenshot
- VLAN configuration screenshots
- EtherChannel verification
- STP verification
- Trunk configuration
- Connectivity test results

## 11. Learning Outcomes

Through this project, I gained practical experience in enterprise network design, VLAN segmentation, IP addressing, redundant switching, EtherChannel, STP, and network troubleshooting.

**Project Status:** Task 2 Completed

**Designed and Implemented using Cisco Packet Tracer.**
