```
aws_tls_ctx_options_init_server_pkcs12(options, allocator, pkcs12, pkcs_password)
```

Initializes options for use in server mode. pkcs12 is a buffer containing a pkcs#12 certificate and private key; it is copied. pkcs_pwd is the corresponding password for the pkcs#12 buffer; it is copied.

NOTE: This only works on Apple devices.

### Prototype

```c
int aws_tls_ctx_options_init_server_pkcs12( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, struct aws_byte_cursor *pkcs12, struct aws_byte_cursor *pkcs_password);
```
