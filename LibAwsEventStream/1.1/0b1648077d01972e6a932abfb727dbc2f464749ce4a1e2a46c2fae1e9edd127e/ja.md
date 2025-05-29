```
aws_event_stream_rpc_server_connection_is_open(connection)
```

接続が開いている場合はtrueを返します。それ以外の場合はfalseを返します。

### プロトタイプ

```c
bool aws_event_stream_rpc_server_connection_is_open( struct aws_event_stream_rpc_server_connection *connection);
```
