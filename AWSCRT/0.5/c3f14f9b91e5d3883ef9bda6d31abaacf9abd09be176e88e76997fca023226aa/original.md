```
MQTTClient(
    tls_ctx::Union{ClientTLSContext,Nothing},
    bootstrap::ClientBootstrap = get_or_create_default_client_bootstrap(),
)
```

MQTT client.

Arguments:

  * `tls_ctx (Union{ClientTLSContext,Nothing})`: TLS context for secure socket connections. If `nothing`, an unencrypted connection is used.
  * `bootstrap (ClientBootstrap) (default=get_or_create_default_client_bootstrap())`: Client bootstrap to use when initiating new socket connections. Uses the singleton by default.
