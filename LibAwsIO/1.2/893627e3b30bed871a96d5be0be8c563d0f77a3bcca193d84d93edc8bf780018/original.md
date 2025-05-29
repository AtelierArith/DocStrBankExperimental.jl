```
aws_socket_assign_to_event_loop(socket, event_loop)
```

Assigns the socket to the event-loop. The socket will begin receiving read/write/error notifications after this call.

Note: If you called connect for TCP or Unix Domain Sockets and received a connection_success callback, this has already happened. You only need to call this function when:

a.) This socket is a server socket (e.g. a result of a call to start_accept()) b.) This socket is a UDP socket.

### Prototype

```c
int aws_socket_assign_to_event_loop(struct aws_socket *socket, struct aws_event_loop *event_loop);
```
