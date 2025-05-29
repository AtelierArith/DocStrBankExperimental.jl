```
aws_http2_stream_get_received_reset_error_code(http2_stream, out_http2_error)
```

rst*streamで受信したエラーコードを取得します。ストリームが完了し、RST*STREAMフレームが受信された場合のみ有効です。

# 引数

  * `http2_stream`: HTTP/2ストリーム。
  * `out_http2_error`: rst_streamで受信したHTTP/2エラーコードを設定するために取得します。

### プロトタイプ

```c
int aws_http2_stream_get_received_reset_error_code(struct aws_http_stream *http2_stream, uint32_t *out_http2_error);
```
