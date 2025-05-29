```
aws_http_connection_new_requests_allowed(connection)
```

Return whether the connection can make a new requests. If false, then a new connection must be established to make further requests.

### Prototype

```c
bool aws_http_connection_new_requests_allowed(const struct aws_http_connection *connection);
```
