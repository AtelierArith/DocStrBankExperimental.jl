```
aws_event_stream_rpc_client_connection_connect(allocator, conn_options)
```

Initiate a new connection. If this function returns AWS_OP_SUCESSS, the [`aws_event_stream_rpc_client_connection_options`](@ref)::on_connection_setup is guaranteed to be called exactly once. If that callback successfully creates a connection, [`aws_event_stream_rpc_client_connection_options`](@ref)::on_connection_shutdown will be invoked upon connection closure. However if the connection was never successfully setup, [`aws_event_stream_rpc_client_connection_options`](@ref)::on_connection_shutdown will not be invoked later.

### Prototype

```c
int aws_event_stream_rpc_client_connection_connect( struct aws_allocator *allocator, const struct aws_event_stream_rpc_client_connection_options *conn_options);
```
