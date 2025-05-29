```
aws_event_stream_rpc_server_connection_send_protocol_message(connection, message_args, flush_fn, user_data)
```

接続上でプロトコルメッセージを送信します（アプリケーションデータではありません）。メッセージが有効で、チャネルに正常に書き込まれた場合、flush_fnが呼び出されます。

### プロトタイプ

```c
int aws_event_stream_rpc_server_connection_send_protocol_message( struct aws_event_stream_rpc_server_connection *connection, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_server_message_flush_fn *flush_fn, void *user_data);
```
