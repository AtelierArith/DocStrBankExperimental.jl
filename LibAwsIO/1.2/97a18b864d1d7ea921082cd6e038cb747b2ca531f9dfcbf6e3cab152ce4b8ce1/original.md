```
aws_tls_ctx_options_init_server_pkcs12_from_path(options, allocator, pkcs12_path, pkcs_password)
```

Initializes options for use in server mode. pkcs12_path is a path to a file on disk containing a pkcs#12 file. The file is loaded into an internal buffer. pkcs_pwd is the corresponding password for the pkcs#12 file; it is copied.

NOTE: This only works on Apple devices.

### Prototype

```c
int aws_tls_ctx_options_init_server_pkcs12_from_path( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const char *pkcs12_path, struct aws_byte_cursor *pkcs_password);
```
