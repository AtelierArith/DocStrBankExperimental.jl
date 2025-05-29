```
aws_custom_key_op_handler_acquire(key_op_handler)
```

渡された [`aws_custom_key_op_handler`](@ref) の参照カウントを増加させ、それを返します。

### プロトタイプ

```c
struct aws_custom_key_op_handler *aws_custom_key_op_handler_acquire( struct aws_custom_key_op_handler *key_op_handler);
```
