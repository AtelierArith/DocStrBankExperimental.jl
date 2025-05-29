```
aws_event_stream_rpc_client_connection_close(connection, shutdown_error_code)
```

接続が開いている場合は接続を閉じ、[`aws_event_stream_rpc_client_connection_options`](@ref)::on*connection*shutdownがシャットダウン時に呼び出されます。shutdown*error*codeはシャットダウンの理由を示します。正常にシャットダウンするには0またはAWS*ERROR*SUCCESSを渡してください。

### プロトタイプ

```c
void aws_event_stream_rpc_client_connection_close( struct aws_event_stream_rpc_client_connection *connection, int shutdown_error_code);
```
