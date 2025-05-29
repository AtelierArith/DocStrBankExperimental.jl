```
aws_http_connection_close(connection)
```

Begin shutdown sequence of the connection if it hasn't already started. This will schedule shutdown tasks on the EventLoop that may send HTTP/TLS/TCP shutdown messages to peers if necessary, and will eventually cause internal connection memory to stop being accessed and on_shutdown() callback to be called.

It's safe to call this function regardless of the connection state as long as you hold a reference to the connection.

### Prototype

```c
void aws_http_connection_close(struct aws_http_connection *connection);
```
