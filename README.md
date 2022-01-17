**Pi-Hole & DNSCrypt-Proxy DoH (DNS-over-HTTPS) Docker**
=============

Pi-hole & DoH made super easy.

This project is based on the [pihole-doh](https://github.com/AzamServer/pihole-doh) by Ali Azam. It's modified to use [dnscrypt-proxy 2](https://github.com/DNSCrypt/dnscrypt-proxy) instead of cloudflared. I found it much more convenient to use.

It's currently tested to work on Ubuntu 18.04 LTS server. The base image is based on the latest Pi-hole, using dnscrypt-proxy v2.1.1. You may want to modify the Dockerfile for other configurations.

Default Configuration
---

- Exposed ports:
  - 53 (DNS)
  - 80 (Web admin)
- Port 67 (DHCP) is disabled by default.

How to Use
---

- Install docker-compose in the host computer.
- Make sure that exposed ports are not in use in the host computer.
- Clone the project.
- Modify configurations as necessary:
  - Particularly you may want to modify `server_names` variable in `dnscrypt-proxy.toml`.
  - The list of supported public servers can be found [on the project's website](https://dnscrypt.info/public-servers).
- Run docker-compose with sudo.
- Change web admin password (default is `admin`):
  ```bash
  sudo docker exec -it $DOCKER_NAME pihole -a -p
  ```  
  where `pihole-dnscrypt` is the default for `$DOCKER_NAME`.
- Enjoy!
