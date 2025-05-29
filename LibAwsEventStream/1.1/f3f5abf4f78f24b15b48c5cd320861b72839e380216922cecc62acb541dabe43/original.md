```
aws_event_stream_rpc_server_continuation_is_closed(continuation)
```

returns true if the continuation is still in an open state.

### Prototype

```c
bool aws_event_stream_rpc_server_continuation_is_closed( struct aws_event_stream_rpc_server_continuation_token *continuation);
```
