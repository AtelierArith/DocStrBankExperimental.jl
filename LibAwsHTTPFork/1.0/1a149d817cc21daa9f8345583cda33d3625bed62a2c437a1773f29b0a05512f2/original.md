```
aws_http_connection_configure_server(connection, options)
```

Configure a server connection. This must be called from the server's on_incoming_connection callback.

### Prototype

```c
int aws_http_connection_configure_server( struct aws_http_connection *connection, const struct aws_http_server_connection_options *options);
```
