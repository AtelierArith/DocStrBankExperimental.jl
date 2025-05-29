```
aws_http_connection_get_channel(connection)
```

Returns the channel hosting the HTTP connection. Do not expose this function to language bindings.

### Prototype

```c
struct aws_channel *aws_http_connection_get_channel(struct aws_http_connection *connection);
```
