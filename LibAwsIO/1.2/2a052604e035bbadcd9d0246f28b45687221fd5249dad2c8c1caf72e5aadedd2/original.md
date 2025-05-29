```
aws_tls_ctx_options_init_client_mtls(options, allocator, cert, pkey)
```

Initializes options for use with mutual tls in client mode. cert and pkey are copied. cert and pkey are treated as PKCS#7 PEM armored.

### Prototype

```c
int aws_tls_ctx_options_init_client_mtls( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const struct aws_byte_cursor *cert, const struct aws_byte_cursor *pkey);
```
