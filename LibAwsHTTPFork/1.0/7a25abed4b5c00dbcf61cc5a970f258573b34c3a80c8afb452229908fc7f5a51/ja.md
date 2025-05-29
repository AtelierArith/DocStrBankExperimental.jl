```
aws_http_stream_activate(stream)
```

クライアントが開始したストリーム専用（[`aws_http_connection_make_request`](@ref) の呼び出し直後に続く）。

リクエストの送信ストリーム処理をアクティブにします。

### プロトタイプ

```c
int aws_http_stream_activate(struct aws_http_stream *stream);
```
