```
aws_tls_key_operation_complete_with_error(operation, error_code)
```

Complete an failed TLS private key operation. The TLS connection will fail. The operation is freed by this call.

You MUST call this or [`aws_tls_key_operation_complete`](@ref)(). Failure to do so will stall the TLS connection indefinitely and leak memory.

### Prototype

```c
void aws_tls_key_operation_complete_with_error(struct aws_tls_key_operation *operation, int error_code);
```
