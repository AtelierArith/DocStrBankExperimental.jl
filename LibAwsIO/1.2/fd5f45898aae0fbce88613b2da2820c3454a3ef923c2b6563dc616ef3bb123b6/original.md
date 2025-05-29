```
aws_custom_key_op_handler_acquire(key_op_handler)
```

Increases the reference count for the passed-in [`aws_custom_key_op_handler`](@ref) and returns it.

### Prototype

```c
struct aws_custom_key_op_handler *aws_custom_key_op_handler_acquire( struct aws_custom_key_op_handler *key_op_handler);
```
