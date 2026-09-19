# Hestia Domain Control Panel

HestiaCP normally serves its control panel on port `8083`, resulting in an address such as:

```
https://server.example.com:8083
```

This repository contains a pair of HestiaCP Nginx proxy templates that allow a web domain to proxy requests to the Hestia control panel instead. This makes it possible to access the panel using a normal HTTPS address such as:

```
https://cp.example.com
```

The templates use Hestia's existing proxy template functionality and leave the control panel itself listening on port `8083` internally.

## Templates

- `cp.tpl` redirects HTTP requests to HTTPS.
- `cp.stpl` proxies HTTPS requests to the Hestia control panel at `https://127.0.0.1:8083`.

## Installation

These templates are intended for HestiaCP installations using Nginx proxy templates.

Download the templates to Hestia's Nginx proxy template directory:

```
sudo wget \
  -O /usr/local/hestia/data/templates/web/nginx/cp.tpl \
  https://raw.githubusercontent.com/ryanbrownell/Hestia-Domain-Control-Panel/main/cp.tpl

sudo wget \
  -O /usr/local/hestia/data/templates/web/nginx/cp.stpl \
  https://raw.githubusercontent.com/ryanbrownell/Hestia-Domain-Control-Panel/main/cp.stpl
```

Then:

1. Create or edit the web domain that will serve the Hestia control panel.
2. Enable SSL and obtain a Let's Encrypt certificate for the domain.
3. Select `cp` as the domain's **Proxy Template**.
4. Save the domain.

The Hestia control panel should then be available at the HTTPS URL for that domain.
