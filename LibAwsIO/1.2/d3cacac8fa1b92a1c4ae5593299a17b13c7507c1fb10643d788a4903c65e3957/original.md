```
aws_custom_key_op_handler_perform_operation(key_op_handler, operation)
```

Calls the on_key_operation vtable function. See [`aws_custom_key_op_handler_vtable`](@ref) for function details.

### Prototype

```c
void aws_custom_key_op_handler_perform_operation( struct aws_custom_key_op_handler *key_op_handler, struct aws_tls_key_operation *operation);
```
