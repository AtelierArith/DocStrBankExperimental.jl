```
aws_tls_ctx_options_set_extension_data(options, extension_data)
```

When implementing BYO_CRYPTO, if you need extra data to pass to your tls implementation, set it here. The lifetime of extension_data must outlive the options object and be cleaned up after options is cleaned up.

### Prototype

```c
void aws_tls_ctx_options_set_extension_data(struct aws_tls_ctx_options *options, void *extension_data);
```
