```
aws_tls_key_operation_complete(operation, output)
```

Complete a successful TLS private key operation by providing its output. The output is copied into the TLS connection. The operation is freed by this call.

You MUST call this or [`aws_tls_key_operation_complete_with_error`](@ref)(). Failure to do so will stall the TLS connection indefinitely and leak memory.

### Prototype

```c
void aws_tls_key_operation_complete(struct aws_tls_key_operation *operation, struct aws_byte_cursor output);
```
