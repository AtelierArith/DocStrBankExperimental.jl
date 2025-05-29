```
aws_event_stream_rpc_server_connection_from_existing_channel(server, channel, connection_options)
```

サーバーをバイパスし、既存のチャネル上に接続を作成します。返される接続に対して接続ライフタイムコールバックは呼び出されません。エラーが発生した場合はNULLを返します。このAPIを使用する場合に限り、返される接続はすでに参照カウントされており、[`aws_event_stream_rpc_server_connection_acquire`](@ref)()を明示的に呼び出していなくても、[`aws_event_stream_rpc_server_connection_release`](@ref)()を呼び出す必要があります。

### プロトタイプ

```c
struct aws_event_stream_rpc_server_connection * aws_event_stream_rpc_server_connection_from_existing_channel( struct aws_event_stream_rpc_server_listener *server, struct aws_channel *channel, const struct aws_event_stream_rpc_connection_options *connection_options);
```
