TOML

[upstream.0]
  name = "Control D"
  type = "doh"
  endpoint = "https://dns.controld.com/YOUR_RESOLVER_ID"
  timeout = 5000

[upstream.1]
  name = "Local dnsmasq"
  type = "legacy"
  endpoint = "127.0.0.1:5354"
  timeout = 1000

[listener.0]
  ip = "127.0.0.1"
  port = 53

[listener.0.policy]
  rules = [
    {"target" = ["upstream.1"]},
    {"*.target" = ["upstream.1"]},
    {"internal" = ["upstream.1"]},
    {"*.internal" = ["upstream.1"]},
  ]
