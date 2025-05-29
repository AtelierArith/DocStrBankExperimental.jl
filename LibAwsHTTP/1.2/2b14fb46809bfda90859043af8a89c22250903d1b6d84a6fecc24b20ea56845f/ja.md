```
aws_http_stream_new_server_request_handler(options)
```

リクエストを受信し応答するサーバー接続を持つストリームを作成します。この関数は、[`aws_http_on_incoming_request_fn`](@ref) コールバックからのみ呼び出すことができます。応答を送信するには、[`aws_http_stream_send_response`](@ref)() を使用する必要があります。

### プロトタイプ

```c
struct aws_http_stream *aws_http_stream_new_server_request_handler( const struct aws_http_request_handler_options *options);
```
