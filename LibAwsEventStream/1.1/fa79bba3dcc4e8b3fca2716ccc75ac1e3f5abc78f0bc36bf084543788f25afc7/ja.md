```
aws_event_stream_rpc_client_connection_connect(allocator, conn_options)
```

新しい接続を開始します。この関数が AWS*OP*SUCCESS を返す場合、[`aws_event_stream_rpc_client_connection_options`](@ref)::on*connection*setup は正確に1回呼び出されることが保証されます。そのコールバックが接続を正常に作成した場合、[`aws_event_stream_rpc_client_connection_options`](@ref)::on*connection*shutdown は接続のクローズ時に呼び出されます。ただし、接続が正常に設定されなかった場合、[`aws_event_stream_rpc_client_connection_options`](@ref)::on*connection*shutdown は後で呼び出されることはありません。

### プロトタイプ

```c
int aws_event_stream_rpc_client_connection_connect( struct aws_allocator *allocator, const struct aws_event_stream_rpc_client_connection_options *conn_options);
```
