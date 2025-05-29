```
aws_http2_headers_set_request_authority(h2_headers, authority)
```

`:authority` を設定します（リクエスト擬似ヘッダーのみ）。擬似ヘッダーは、基になる文字列のコピーを作成します。

### プロトタイプ

```c
int aws_http2_headers_set_request_authority(struct aws_http_headers *h2_headers, struct aws_byte_cursor authority);
```
