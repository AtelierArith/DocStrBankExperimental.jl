```
aws_tls_ctx_options_init_default_server(options, allocator, cert, pkey)
```

Initializes options for use with in server mode. cert and pkey are copied. cert and pkey are treated as PKCS#7 PEM armored.

### Prototype

```c
int aws_tls_ctx_options_init_default_server( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, struct aws_byte_cursor *cert, struct aws_byte_cursor *pkey);
```
