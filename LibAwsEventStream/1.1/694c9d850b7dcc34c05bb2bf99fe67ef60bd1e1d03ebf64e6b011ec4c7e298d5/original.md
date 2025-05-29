```
aws_event_stream_rpc_client_continuation_is_closed(continuation)
```

returns true if the continuation has been closed.

### Prototype

```c
bool aws_event_stream_rpc_client_continuation_is_closed( const struct aws_event_stream_rpc_client_continuation_token *continuation);
```
