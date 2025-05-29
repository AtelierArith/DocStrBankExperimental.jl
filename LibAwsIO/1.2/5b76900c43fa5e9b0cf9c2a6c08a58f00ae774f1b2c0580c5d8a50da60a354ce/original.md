```
aws_tls_ctx_options_init_client_mtls_from_system_path(options, allocator, cert_reg_path)
```

Initializes options for use with mutual tls in client mode. cert_reg_path is the path to a system installed certficate/private key pair. Example: CurrentUser\MY\<thumprint>

NOTE: This only works on Windows.

### Prototype

```c
int aws_tls_ctx_options_init_client_mtls_from_system_path( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const char *cert_reg_path);
```
