```
aws_tls_ctx_options_init_client_mtls_pkcs12_from_path(options, allocator, pkcs12_path, pkcs_pwd)
```

Initializes options for use with mutual tls in client mode. pkcs12_path is a path to a file on disk containing a pkcs#12 file. The file is loaded into an internal buffer. pkcs_pwd is the corresponding password for the pkcs#12 file; it is copied.

NOTE: This only works on Apple devices.

### Prototype

```c
int aws_tls_ctx_options_init_client_mtls_pkcs12_from_path( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const char *pkcs12_path, const struct aws_byte_cursor *pkcs_pwd);
```
