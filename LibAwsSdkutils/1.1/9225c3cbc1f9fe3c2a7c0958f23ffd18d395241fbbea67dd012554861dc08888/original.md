```
aws_byte_buf_append_resource_name(buf, arn)
```

Serializes an ARN structure into the lexical string format

### Prototype

```c
int aws_byte_buf_append_resource_name(struct aws_byte_buf *buf, const struct aws_resource_name *arn);
```
