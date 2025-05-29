```
aws_socket_is_open(socket)
```

Returns true if the socket is still open (doesn't mean connected or listening, only that it hasn't had close() called.

### Prototype

```c
bool aws_socket_is_open(struct aws_socket *socket);
```
