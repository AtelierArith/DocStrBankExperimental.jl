```
aws_event_stream_rpc_client_connection_is_open(connection)
```

接続が開いている場合はtrueを返し、それ以外の場合はfalseを返します。

### プロトタイプ

```c
bool aws_event_stream_rpc_client_connection_is_open( const struct aws_event_stream_rpc_client_connection *connection);
```
