```
aws_tls_key_operation_get_type(operation)
```

Returns the type of operation that needs to be performed by the custom key operation. If the implementation cannot perform the operation, use [`aws_tls_key_operation_complete_with_error`](@ref)() to preventing stalling the TLS connection.

### Prototype

```c
enum aws_tls_key_operation_type aws_tls_key_operation_get_type(const struct aws_tls_key_operation *operation);
```
