```
aws_http_headers_erase(headers, name)
```

この名前のすべてのヘッダーを削除します。この名前のヘッダーが見つからない場合は、AWS*ERROR*HTTP*HEADER*NOT_FOUNDが発生します。

### プロトタイプ

```c
int aws_http_headers_erase(struct aws_http_headers *headers, struct aws_byte_cursor name);
```
