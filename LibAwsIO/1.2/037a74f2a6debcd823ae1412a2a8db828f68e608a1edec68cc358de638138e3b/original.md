```
aws_socket_close(socket)
```

Calls `close()` on the socket and unregisters all io operations from the event loop. This function must be called from the event-loop's thread unless this is a listening socket. If it's a listening socket it can be called from any non-event-loop thread or the event-loop the socket is currently assigned to. If called from outside the event-loop, this function will block waiting on the socket to close. If this is called from an event-loop thread other than the one it's assigned to, it presents the possibility of a deadlock, so don't do it.

If you are using Apple Network Framework, you should always call this function from an event-loop thread regardless it is a server or client socket.

### Prototype

```c
int aws_socket_close(struct aws_socket *socket);
```
