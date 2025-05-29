```
aws_event_stream_rpc_client_connection_new_stream(connection, continuation_options)
```

新しいストリームを作成します。continuation*optionのコールバックは呼び出されず、[`aws*event*stream*rpc*client*continuation_activate`](@ref)()が呼び出されるまで、何も送信されません。

成功した場合、参照カウントが1の[`aws_event_stream_rpc_client_continuation_token`](@ref)のインスタンスを返します。使用が終わったら、[`aws_event_stream_rpc_client_continuation_release`](@ref)()を呼び出す必要があります。失敗した場合はNULLを返します。

### プロトタイプ

```c
struct aws_event_stream_rpc_client_continuation_token * aws_event_stream_rpc_client_connection_new_stream( struct aws_event_stream_rpc_client_connection *connection, const struct aws_event_stream_rpc_client_stream_continuation_options *continuation_options);
```
