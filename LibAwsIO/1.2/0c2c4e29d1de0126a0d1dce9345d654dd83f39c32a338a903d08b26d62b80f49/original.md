```
aws_tls_key_operation_get_digest_algorithm(operation)
```

Returns the algorithm the operation digest is signed with. If the implementation does not support the digest algorithm, use [`aws_tls_key_operation_complete_with_error`](@ref)() to preventing stalling the TLS connection.

### Prototype

```c
enum aws_tls_hash_algorithm aws_tls_key_operation_get_digest_algorithm(const struct aws_tls_key_operation *operation);
```
