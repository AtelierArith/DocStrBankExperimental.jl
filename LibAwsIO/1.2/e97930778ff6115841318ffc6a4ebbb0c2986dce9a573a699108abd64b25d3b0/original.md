```
aws_tls_ctx_options_override_default_trust_store(options, ca_file)
```

Override the default trust store. ca_file is a buffer containing a PEM armored chain of trusted CA certificates. ca_file is copied.

### Prototype

```c
int aws_tls_ctx_options_override_default_trust_store( struct aws_tls_ctx_options *options, const struct aws_byte_cursor *ca_file);
```
