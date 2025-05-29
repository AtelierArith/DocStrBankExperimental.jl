```
aws_socket_endpoint_init_local_address_for_test(endpoint)
```

Assigns a random address (UUID) for use with AWS_SOCKET_LOCAL (Unix Domain Sockets). For use in internal tests only.

### Prototype

```c
void aws_socket_endpoint_init_local_address_for_test(struct aws_socket_endpoint *endpoint);
```
