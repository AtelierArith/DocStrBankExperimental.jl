```
aws_socket_get_error(socket)
```

Gets the latest error from the socket. If no error has occurred AWS_OP_SUCCESS will be returned. This function does not raise any errors to the installed error handlers.

### Prototype

```c
int aws_socket_get_error(struct aws_socket *socket);
```
