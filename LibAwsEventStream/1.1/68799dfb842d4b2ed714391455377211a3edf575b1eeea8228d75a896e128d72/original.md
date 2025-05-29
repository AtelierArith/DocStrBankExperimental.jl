```
aws_event_stream_rpc_client_connection_close(connection, shutdown_error_code)
```

Closes the connection if it is open and [`aws_event_stream_rpc_client_connection_options`](@ref)::on_connection_shutdown will be invoked upon shutdown. shutdown_error_code will indicate the reason for shutdown. For a graceful shutdown pass 0 or AWS_ERROR_SUCCESS.

### Prototype

```c
void aws_event_stream_rpc_client_connection_close( struct aws_event_stream_rpc_client_connection *connection, int shutdown_error_code);
```
