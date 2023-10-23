---
title: CGNAT
---

Carrier-grade NAT (CGNAT) is a technique used by some ISPs where many customers will share one single IP address, in order to conserve the amount of IPv4 addresses the ISP owns.

Unfortunately, this also means that you will be unable to host a server from home without additional steps, as it won't be directly accessible from the wider Internet.

## Checking for CGNAT
First of all, you need to [find your external IP address](obtain-external-ip). Then follow the steps for your operating system to run a traceroute:

**Windows:**

1. Open a command prompt: Press `Win + X`, type `cmd.exe` and press Enter.
2. Type `tracert <external IP>`.

**Linux:**

1. Open a terminal.
2. Type `traceroute <external IP>` (requires `traceroute` to be installed)

### Analysing the traceroute
Whether you are behind CGNAT or not can be determined based on the amount of hops the traceroute will return. If the traceroute returns a single hop and then finishes then you **are not** behind CGNAT:

```bash
traceroute to 78.71.XX.XX (78.71.XX.XX), 30 hops max, 60 byte packets
 1  78-71-XX-XX.example.org (78.71.XX.XX)  0.567 ms  0.643 ms  0.702 ms
```

However, if there are two or even more hops, or if the traceroute does not complete, then you **are most likely** behind CGNAT and will not be able to host a publicly available server without extra steps.

## If you are behind CGNAT
First of all, try contacting your ISP or check their website. Some ISPs are willing to move you onto a bare IP (may also be referred to as a "public" IP) if requested, by contacting them directly or through a page on their website. If asked for the motivation, say that you want to host a game server.

If they are unwilling to do this, or require you to upgrade to a business plan to provide this service, you will need to either tunnel your server (TODO) or rent a VPS/dedicated in the cloud to host your server on.
