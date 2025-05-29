```
aws_byte_buf_append_resource_name(buf, arn)
```

ARN構造体を字句文字列形式にシリアライズします

### プロトタイプ

```c
int aws_byte_buf_append_resource_name(struct aws_byte_buf *buf, const struct aws_resource_name *arn);
```
