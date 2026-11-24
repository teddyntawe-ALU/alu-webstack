# HTTPS SSL

Securing the web stack with HTTPS: SSL termination on HAProxy and redirection of all HTTP traffic to HTTPS.

| File | Description |
| ---- | ----------- |
| `0-world_wide_web` | Bash script (using `awk` and a function) that shows the record type and destination of a domain's subdomains `www`, `lb-01`, `web-01`, `web-02` |
| `1-haproxy_ssl_termination` | HAProxy config (`/etc/haproxy/haproxy.cfg`) terminating SSL on port 443 for `www` |
| `2-redirect_http_to_https` | HAProxy config that also redirects HTTP to HTTPS with a `301` |

## Key concepts
- **HTTPS** is HTTP over SSL/TLS. SSL provides two main things: **encryption** (nobody in between can read the traffic) and **authentication/identity** (the certificate proves you are talking to the real server).
- **Encrypting traffic** protects passwords, cookies and personal data from being read or modified in transit.
- **SSL termination** means the load balancer decrypts the HTTPS traffic and forwards plain HTTP to the web servers, so they don't have to handle encryption.
