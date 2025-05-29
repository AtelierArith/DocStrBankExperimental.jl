```
aws_http_headers_erase_value(headers, name, value)
```

この名前と値を持つ最初のヘッダーを削除します。該当するヘッダーが見つからない場合は、AWS*ERROR*HTTP*HEADER*NOT_FOUNDが発生します。

### プロトタイプ

```c
int aws_http_headers_erase_value( struct aws_http_headers *headers, struct aws_byte_cursor name, struct aws_byte_cursor value);
```
