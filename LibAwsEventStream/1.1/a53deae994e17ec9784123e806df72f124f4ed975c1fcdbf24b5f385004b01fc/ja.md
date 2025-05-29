```
aws_event_stream_rpc_client_connection_send_protocol_message(connection, message_args, flush_fn, user_data)
```

接続上でメッセージを送信します。これらは接続レベルのメッセージでなければなりません（アプリケーションメッセージではありません）。

flush_fnは、メッセージが正常にワイヤに書き込まれたとき、または失敗したときに呼び出されます。

メッセージが正常に作成され、キューに入れられた場合はAWS*OP*SUCCESSを返し、その場合はflush*fnが常に呼び出されます。それ以外の場合、flush*fnは呼び出されません。

### プロトタイプ

```c
int aws_event_stream_rpc_client_connection_send_protocol_message( struct aws_event_stream_rpc_client_connection *connection, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_client_message_flush_fn *flush_fn, void *user_data);
```
