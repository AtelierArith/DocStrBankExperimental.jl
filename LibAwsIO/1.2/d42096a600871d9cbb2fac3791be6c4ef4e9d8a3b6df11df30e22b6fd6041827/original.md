```
aws_socket_validate_port_for_connect(port, domain)
```

Raises AWS_IO_SOCKET_INVALID_ADDRESS and logs an error if connecting to this port is illegal. For example, port must be in range 1-65535 to connect with IPv4. These port values would fail eventually in [`aws_socket_connect`](@ref)(), but you can use this function to validate earlier.

### Prototype

```c
int aws_socket_validate_port_for_connect(uint32_t port, enum aws_socket_domain domain);
```
