```
aws_http_headers_add_header(headers, header)
```

ヘッダーを追加します。基になる文字列はコピーされます。

### プロトタイプ

```c
int aws_http_headers_add_header(struct aws_http_headers *headers, const struct aws_http_header *header);
```
