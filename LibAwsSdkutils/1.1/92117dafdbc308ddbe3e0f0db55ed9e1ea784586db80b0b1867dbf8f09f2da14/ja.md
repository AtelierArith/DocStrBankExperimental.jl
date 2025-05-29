```
aws_resource_name_init_from_cur(arn, input)
```

ARN "Amazon Resource Name" を表す構造体をメモリ内に表現したものを与えます

### プロトタイプ

```c
int aws_resource_name_init_from_cur(struct aws_resource_name *arn, const struct aws_byte_cursor *input);
```
