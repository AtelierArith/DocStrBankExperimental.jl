```
aws_http2_headers_set_request_scheme(h2_headers, scheme)
```

`:scheme` を設定します（リクエスト擬似ヘッダーのみ）。擬似ヘッダーは、基になる文字列の独自のコピーを作成します。

### プロトタイプ

```c
int aws_http2_headers_set_request_scheme(struct aws_http_headers *h2_headers, struct aws_byte_cursor scheme);
```
