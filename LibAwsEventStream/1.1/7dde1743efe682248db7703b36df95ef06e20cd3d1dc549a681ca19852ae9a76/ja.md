```
aws_event_stream_rpc_client_continuation_send_message(continuation, message_args, flush_fn, user_data)
```

継続にメッセージを送信します。[`aws_event_stream_rpc_client_continuation_activate`](@ref)()は、この関数を呼び出す前に正常に呼び出される必要があります。

この関数がAWS*OP*SUCCESSを返すと、メッセージがワイヤに書き込まれるか、失敗した場合にflush_fnが呼び出されます。

### プロトタイプ

```c
int aws_event_stream_rpc_client_continuation_send_message( struct aws_event_stream_rpc_client_continuation_token *continuation, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_client_message_flush_fn *flush_fn, void *user_data);
```
