```
aws_custom_key_op_handler_release(key_op_handler)
```

渡された [`aws_custom_key_op_handler`](@ref) の参照カウントを減少させ、NULLを返します。

### プロトタイプ

```c
struct aws_custom_key_op_handler *aws_custom_key_op_handler_release( struct aws_custom_key_op_handler *key_op_handler);
```
