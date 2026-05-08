# Nora-Net

A self-hosted home network and server environment — designed, built, and maintained as a personal infrastructure project. Every component is documented in a self-hosted BookStack wiki (internal access only).

All devices and services follow a **Horizon Zero Dawn** naming convention.

---

## Hardware

### Servers

| Hostname | Role |
|----------|------|
| `zero-dawn` | Primary Storage Server — ZFS storage pool |
| `minerva` | Primary Docker Host — also runs a ZFS storage pool |

### Network Equipment

| Hostname | Role |
|----------|------|
| `fireclaw` | pfSense Firewall & Router |
| TP-Link Managed Switch | Wired switching |
| `tallnecks` | Deco M9 Mesh Wi-Fi |

---

## Network

- **Local domain:** `nora.local`
- **External domain:** `noratribe.duckdns.org` (DuckDNS dynamic DNS)
- **Firewall/routing:** pfSense (`fireclaw`)
- **IP addressing:** Documented across network equipment, computers, mobile devices, game consoles, TVs, and smart home devices
- **VLANs:** Planned/in progress

---

## DNS Stack

| Hostname | Role |
|----------|------|
| `thunderjaw` | Primary Pi-hole — network-wide ad blocking |
| `stormbird` | Backup Pi-hole (Raspberry Pi — pending deployment) |
| `demeter` | Unbound — recursive DNS resolver |

DNS queries flow: clients → Pi-hole (ad filtering) → Unbound (recursive resolution direct to root servers, no upstream forwarder).

---

## Active Services (Docker — hosted on `minerva`)

| Container | Stack | Role |
|-----------|-------|------|
| `portainer` | portainer | Docker management UI |
| `wetty` | shell-walker | Browser-based SSH terminal |
| `uptime-kuma` | watcher | Uptime & service monitoring |
| `thunderjaw` | thunderjaw | Pi-hole — DNS-level ad blocking |
| `unbound` | demeter | Recursive DNS resolver |
| `nginx-proxy-manager` | meridian | Reverse proxy & SSL termination |
| `ntfy` | glinthawk | Self-hosted push notification server |
| `mariadb` | apollo | MariaDB database server |
| `bookstack` | apollo | Self-hosted wiki & documentation |
| `bookstack-static` | static | Static file server |
| `frostclaw-frontend` | frostclaw | Custom app — financial coaching app (frontend) |
| `frostclaw-backend` | frostclaw | Custom app — financial coaching app (backend) |
| `mossynook-ui` | mossynook | Custom app — craft business inventory & sales tracker (frontend) |
| `mossynook-backend` | mossynook | Custom app — craft business inventory & sales tracker (backend) |

---

## Game Servers (hosted on `zero-dawn`)

| Game | Status |
|------|--------|
| Satisfactory | Active |
| Enshrouded | Inactive |
| Valheim | Inactive |

---

## Remote Access

- **Tailscale** — zero-config mesh VPN for secure remote access to all nodes
- **Nginx Proxy Manager** — reverse proxy with SSL for internal service access via `noratribe.duckdns.org`
- **WeTTY** — browser-based SSH terminal for in-browser access to hosts

---

## Storage

- **ZFS** storage pools managed on both `zero-dawn` (primary storage server) and `minerva` (Docker host)
- Documented ZFS pool layout, dataset structure, and backup/recovery procedures

---

## Documentation

All components — hardware specs, service configs, network topology, IP scheme, DNS setup, and runbooks — are documented in a self-hosted **BookStack** wiki organized into the following books:

- Infrastructure Overview
- Network & DNS
- Services & Containers
- Backup & Recovery
- Processes
- Troubleshooting
- Change Log

The wiki is accessible internally via `nora.local` and remotely via Tailscale.

---

## Planned

- Nextcloud — file sync & collaboration
- Security camera backend

---

## Notes

This repo serves as a public-facing overview of the Nora-Net stack. Configuration files, IP addressing, and sensitive details are maintained privately in the internal BookStack wiki. If you have questions about any component or want to discuss the architecture, feel free to open an issue or reach out via [LinkedIn](https://www.linkedin.com/in/roger-castro-jr/).
