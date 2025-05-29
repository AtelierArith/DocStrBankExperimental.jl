```
aws_http_headers_add_array(headers, array, count)
```

ヘッダーの配列を追加します。基になる文字列はコピーされます。

### プロトタイプ

```c
int aws_http_headers_add_array(struct aws_http_headers *headers, const struct aws_http_header *array, size_t count);
```
