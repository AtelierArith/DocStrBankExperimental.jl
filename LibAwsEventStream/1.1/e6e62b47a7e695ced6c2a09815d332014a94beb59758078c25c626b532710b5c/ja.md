```
aws_event_stream_rpc_client_continuation_activate(continuation, operation_name, message_args, flush_fn, user_data)
```

実際に初期ストリームをピアに送信します。この関数が AWS*OP*SUCCESS を返すと、[`aws_event_stream_rpc_client_connection_new_stream`](@ref)() からのコールバックが実際に呼び出されます。そうでない場合、ストリームはキューに追加されておらず、コールバックは呼び出されません。

operation*name は、ピアとの間で開始したい論理 RPC 呼び出しを識別するための名前です。空であってはなりません。flush*fn は、メッセージがワイヤに書き込まれるか、失敗した場合に呼び出されます。

### プロトタイプ

```c
int aws_event_stream_rpc_client_continuation_activate( struct aws_event_stream_rpc_client_continuation_token *continuation, struct aws_byte_cursor operation_name, const struct aws_event_stream_rpc_message_args *message_args, aws_event_stream_rpc_client_message_flush_fn *flush_fn, void *user_data);
```
