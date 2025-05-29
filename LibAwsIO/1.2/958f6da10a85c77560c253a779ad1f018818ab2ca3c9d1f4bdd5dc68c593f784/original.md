```
aws_tls_ctx_options_override_default_trust_store_from_path(options, ca_path, ca_file)
```

Override the default trust store. ca_path is a path to a directory on disk containing trusted certificates. This is only supported on Unix systems (otherwise this parameter is ignored). ca_file is a path to a file on disk containing trusted certificates. ca_file is loaded from disk and stored in an internal buffer.

### Prototype

```c
int aws_tls_ctx_options_override_default_trust_store_from_path( struct aws_tls_ctx_options *options, const char *ca_path, const char *ca_file);
```
