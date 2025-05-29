```
aws_http2_stream_reset(http2_stream, http2_error)
```

HTTP/2ストリームをリセットします（HTTP/2のみ）。この非同期呼び出しが完全に処理される前にストリームが閉じた場合、RST_STREAMフレームは送信されません。

# 引数

  * `http2_stream`: HTTP/2ストリーム。
  * `http2_error`: [`aws_http2_error_code`](@ref)。ストリームをリセットする理由。

### プロトタイプ

```c
int aws_http2_stream_reset(struct aws_http_stream *http2_stream, uint32_t http2_error);
```
