```
aws_http_server_get_listener_endpoint(server)
```

Returns the local listener endpoint of the HTTP server. Only valid as long as the server remains valid.

### Prototype

```c
const struct aws_socket_endpoint *aws_http_server_get_listener_endpoint(const struct aws_http_server *server);
```
