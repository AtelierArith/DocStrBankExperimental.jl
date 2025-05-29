```
aws_tls_key_operation_get_signature_algorithm(operation)
```

Returns the algorithm the operation is expected to be operated with. If the implementation does not support the signature algorithm, use [`aws_tls_key_operation_complete_with_error`](@ref)() to preventing stalling the TLS connection.

### Prototype

```c
enum aws_tls_signature_algorithm aws_tls_key_operation_get_signature_algorithm( const struct aws_tls_key_operation *operation);
```
