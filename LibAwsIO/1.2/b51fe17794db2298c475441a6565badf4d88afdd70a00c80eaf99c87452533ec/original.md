```
aws_socket_get_bound_address(socket, out_address)
```

Get the local address which the socket is bound to. Raises an error if no address is bound.

### Prototype

```c
int aws_socket_get_bound_address(const struct aws_socket *socket, struct aws_socket_endpoint *out_address);
```
