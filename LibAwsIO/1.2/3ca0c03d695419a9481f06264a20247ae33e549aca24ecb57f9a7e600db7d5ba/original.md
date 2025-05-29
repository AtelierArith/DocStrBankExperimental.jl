```
aws_custom_key_op_handler_release(key_op_handler)
```

Decreases the reference count for the passed-in [`aws_custom_key_op_handler`](@ref) and returns NULL.

### Prototype

```c
struct aws_custom_key_op_handler *aws_custom_key_op_handler_release( struct aws_custom_key_op_handler *key_op_handler);
```
