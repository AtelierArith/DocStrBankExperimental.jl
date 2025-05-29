```
aws_event_stream_rpc_server_connection_close(connection, shutdown_error_code)
```

Closes the connection (including all continuations on the connection), and releases the connection ref count. shutdown_error_code is the error code to use when shutting down the channel. Use AWS_ERROR_SUCCESS for non-error cases.

### Prototype

```c
void aws_event_stream_rpc_server_connection_close( struct aws_event_stream_rpc_server_connection *connection, int shutdown_error_code);
```
