```
aws_socket_read(socket, buffer, amount_read)
```

Reads from the socket. This call is non-blocking and will return `AWS_IO_SOCKET_READ_WOULD_BLOCK` if no data is available. `read` is the amount of data read into `buffer`.

Attempts to read enough to fill all remaining space in the buffer, from `buffer->len` to `buffer->capacity`. `buffer->len` is updated to reflect the buffer's new length.

Use [`aws_socket_subscribe_to_readable_events`](@ref)() to receive notifications of when the socket goes readable.

NOTE! This function must be called from the event-loop used in [`aws_socket_assign_to_event_loop`](@ref)

### Prototype

```c
int aws_socket_read(struct aws_socket *socket, struct aws_byte_buf *buffer, size_t *amount_read);
```
