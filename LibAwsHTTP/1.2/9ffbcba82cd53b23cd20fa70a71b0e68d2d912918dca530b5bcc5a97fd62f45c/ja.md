```
aws_http2_headers_set_request_path(h2_headers, path)
```

`:path`を設定します（リクエスト擬似ヘッダーのみ）。擬似ヘッダーは、基になる文字列のコピーを作成します。

### プロトタイプ

```c
int aws_http2_headers_set_request_path(struct aws_http_headers *h2_headers, struct aws_byte_cursor path);
```
