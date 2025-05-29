```
aws_event_stream_rpc_server_continuation_is_closed(continuation)
```

は、継続がまだオープン状態である場合にtrueを返します。

### プロトタイプ

```c
bool aws_event_stream_rpc_server_continuation_is_closed( struct aws_event_stream_rpc_server_continuation_token *continuation);
```
