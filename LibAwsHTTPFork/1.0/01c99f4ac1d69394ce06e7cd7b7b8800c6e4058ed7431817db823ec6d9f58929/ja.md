```
aws_http_headers_erase_index(headers, index)
```

指定されたインデックスのヘッダーを削除します。

インデックスが無効な場合、AWS*ERROR*INVALID_INDEXが発生します。

### プロトタイプ

```c
int aws_http_headers_erase_index(struct aws_http_headers *headers, size_t index);
```
