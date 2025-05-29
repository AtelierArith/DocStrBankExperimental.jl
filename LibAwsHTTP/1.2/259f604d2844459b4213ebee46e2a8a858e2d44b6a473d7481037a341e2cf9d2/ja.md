```
aws_http_headers_has(headers, name)
```

ヘッダー名がヘッダーに存在するかどうかをテストします

### プロトタイプ

```c
bool aws_http_headers_has(const struct aws_http_headers *headers, struct aws_byte_cursor name);
```
