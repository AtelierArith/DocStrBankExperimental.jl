```
aws_socket_write(socket, cursor, written_fn, user_data)
```

Writes to the socket. This call is non-blocking and will attempt to write as much as it can, but will queue any remaining portion of the data for write when available. written_fn will be invoked once the entire cursor has been written, or the write failed or was cancelled.

NOTE! This function must be called from the event-loop used in [`aws_socket_assign_to_event_loop`](@ref)

For client sockets, connect() and [`aws_socket_assign_to_event_loop`](@ref)() must be called before calling this.

For incoming sockets from a listener, [`aws_socket_assign_to_event_loop`](@ref)() must be called first.

### Prototype

```c
int aws_socket_write( struct aws_socket *socket, const struct aws_byte_cursor *cursor, aws_socket_on_write_completed_fn *written_fn, void *user_data);
```
