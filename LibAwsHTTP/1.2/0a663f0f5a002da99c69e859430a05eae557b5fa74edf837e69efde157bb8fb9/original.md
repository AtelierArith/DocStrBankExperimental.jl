```
aws_http_connection_release(connection)
```

Users must release the connection when they are done with it. The connection's memory cannot be reclaimed until this is done. If the connection was not already shutting down, it will be shut down.

Users should always wait for the on_shutdown() callback to be called before releasing any data passed to the http_connection (Eg `aws_tls_connection_options`, `aws_socket_options`) otherwise there will be race conditions between http_connection shutdown tasks and memory release tasks, causing Segfaults.

### Prototype

```c
void aws_http_connection_release(struct aws_http_connection *connection);
```
