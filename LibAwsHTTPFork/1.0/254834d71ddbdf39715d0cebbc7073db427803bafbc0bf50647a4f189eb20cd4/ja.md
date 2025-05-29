```
aws_http2_stream_get_sent_reset_error_code(http2_stream, out_http2_error)
```

RST*STREAMフレームで送信されたHTTP/2エラーコードを取得します（HTTP/2のみ）。ストリームが完了し、RST*STREAMフレームを送信した場合にのみ有効です。

# 引数

  * `http2_stream`: HTTP/2ストリーム。
  * `out_http2_error`: rst_streamで送信されたHTTP/2エラーコードを設定するために取得します。

### プロトタイプ

```c
int aws_http2_stream_get_sent_reset_error_code(struct aws_http_stream *http2_stream, uint32_t *out_http2_error);
```
