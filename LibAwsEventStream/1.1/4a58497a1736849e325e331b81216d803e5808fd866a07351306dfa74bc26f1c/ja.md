```
aws_event_stream_rpc_server_connection_close(connection, shutdown_error_code)
```

接続を閉じ（接続上のすべての継続を含む）、接続の参照カウントを解放します。shutdown*error*codeは、チャネルをシャットダウンする際に使用するエラーコードです。エラーがない場合はAWS*ERROR*SUCCESSを使用してください。

### プロトタイプ

```c
void aws_event_stream_rpc_server_connection_close( struct aws_event_stream_rpc_server_connection *connection, int shutdown_error_code);
```
