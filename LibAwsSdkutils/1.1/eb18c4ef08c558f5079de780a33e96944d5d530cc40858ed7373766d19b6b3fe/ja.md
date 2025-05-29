```
aws_resource_name_length(arn, size)
```

ARNをバイトバッファに書き込むために必要なスペースを計算します

### プロトタイプ

```c
int aws_resource_name_length(const struct aws_resource_name *arn, size_t *size);
```
