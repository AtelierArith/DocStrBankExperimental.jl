```
aws_http_headers_get(headers, name, out_value)
```

この名前の最初の値を取得し、追加の値は無視します。名前が見つからない場合はAWS*ERROR*HTTP*HEADER*NOT_FOUNDが発生します。

### プロトタイプ

```c
int aws_http_headers_get( const struct aws_http_headers *headers, struct aws_byte_cursor name, struct aws_byte_cursor *out_value);
```
