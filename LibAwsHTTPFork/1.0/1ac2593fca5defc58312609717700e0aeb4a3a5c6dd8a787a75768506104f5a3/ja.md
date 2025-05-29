```
aws_http_headers_add(headers, name, value)
```

ヘッダーを追加します。基になる文字列はコピーされます。

### プロトタイプ

```c
int aws_http_headers_add(struct aws_http_headers *headers, struct aws_byte_cursor name, struct aws_byte_cursor value);
```
