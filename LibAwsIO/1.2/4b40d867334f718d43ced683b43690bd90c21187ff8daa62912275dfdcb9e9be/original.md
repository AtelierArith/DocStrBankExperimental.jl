```
aws_tls_ctx_options_set_verify_peer(options, verify_peer)
```

Enables or disables x.509 validation. Disable this only for testing. To enable mutual TLS in server mode, set verify_peer to true.

### Prototype

```c
void aws_tls_ctx_options_set_verify_peer(struct aws_tls_ctx_options *options, bool verify_peer);
```
