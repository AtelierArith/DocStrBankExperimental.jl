```
aws_event_stream_rpc_server_new_listener(allocator, options)
```

Creates a listener with a ref count of 1. You are responsible for calling [`aws_event_stream_rpc_server_listener_release`](@ref)() when you're finished with the listener. Returns NULL if an error occurs.

### Prototype

```c
struct aws_event_stream_rpc_server_listener *aws_event_stream_rpc_server_new_listener( struct aws_allocator *allocator, struct aws_event_stream_rpc_server_listener_options *options);
```
