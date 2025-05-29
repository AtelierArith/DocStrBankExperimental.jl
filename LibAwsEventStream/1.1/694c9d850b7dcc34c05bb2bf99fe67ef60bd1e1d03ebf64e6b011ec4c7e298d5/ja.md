```
aws_event_stream_rpc_client_continuation_is_closed(continuation)
```

は、継続が閉じられている場合にtrueを返します。

### プロトタイプ

```c
bool aws_event_stream_rpc_client_continuation_is_closed( const struct aws_event_stream_rpc_client_continuation_token *continuation);
```
