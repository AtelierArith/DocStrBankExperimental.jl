```
aws_http2_headers_get_response_status(h2_headers, out_status_code)
```

`:status`を取得します（レスポンス擬似ヘッダーのみ）。ステータスが設定されていない場合、AWS*ERROR*HTTP*DATA*NOT_AVAILABLEが発生します。

### プロトタイプ

```c
int aws_http2_headers_get_response_status(const struct aws_http_headers *h2_headers, int *out_status_code);
```
