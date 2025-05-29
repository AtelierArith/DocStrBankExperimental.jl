```
aws_socket_clean_up(socket)
```

Shuts down any pending operations on the socket, and cleans up state. The socket object can be re-initialized after this operation. This function calls [`aws_socket_close`](@ref). If you have not already called [`aws_socket_close`](@ref)() on the socket, all of the rules for [`aws_socket_close`](@ref)() apply here. In this case it will not fail if you use the function improperly, but on some platforms you will certainly leak memory.

If the socket has already been closed, you can safely, call this from any thread.

### Prototype

```c
void aws_socket_clean_up(struct aws_socket *socket);
```
