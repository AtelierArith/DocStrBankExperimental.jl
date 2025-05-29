```
aws_http2_headers_set_request_method(h2_headers, method)
```

`:method`を設定します（HTTP/2ヘッダーのみ）。ヘッダーは基になる文字列のコピーを作成します。

### プロトタイプ

```c
int aws_http2_headers_set_request_method(struct aws_http_headers *h2_headers, struct aws_byte_cursor method);
```
