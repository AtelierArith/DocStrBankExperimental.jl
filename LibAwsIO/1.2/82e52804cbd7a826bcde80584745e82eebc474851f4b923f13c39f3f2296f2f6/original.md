```
aws_tls_ctx_options_init_client_mtls_from_path(options, allocator, cert_path, pkey_path)
```

Initializes options for use with mutual tls in client mode. cert_path and pkey_path are paths to files on disk. cert_path and pkey_path are treated as PKCS#7 PEM armored. They are loaded from disk and stored in buffers internally.

### Prototype

```c
int aws_tls_ctx_options_init_client_mtls_from_path( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const char *cert_path, const char *pkey_path);
```
