```
aws_socket_validate_port_for_bind(port, domain)
```

Raises AWS_IO_SOCKET_INVALID_ADDRESS and logs an error if binding to this port is illegal. For example, port must in range 0-65535 to bind with IPv4. These port values would fail eventually in [`aws_socket_bind`](@ref)(), but you can use this function to validate earlier.

### Prototype

```c
int aws_socket_validate_port_for_bind(uint32_t port, enum aws_socket_domain domain);
```
