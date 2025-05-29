```
aws_tls_ctx_options_init_client_mtls_with_custom_key_operations(options, allocator, custom, cert_file_contents)
```

Initializes options for use with mutual TLS in client mode, where private key operations are handled by custom code.

Note: cert_file_contents will be copied into a new buffer after this function is called, so you do not need to keep that data alive after calling this function.

# Arguments

  * `options`: [`aws_tls_ctx_options`](@ref) to be initialized.
  * `allocator`: Allocator to use.
  * `custom`: Options for custom key operations.
  * `cert_file_contents`: The contents of a certificate file.

### Prototype

```c
int aws_tls_ctx_options_init_client_mtls_with_custom_key_operations( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, struct aws_custom_key_op_handler *custom, const struct aws_byte_cursor *cert_file_contents);
```
