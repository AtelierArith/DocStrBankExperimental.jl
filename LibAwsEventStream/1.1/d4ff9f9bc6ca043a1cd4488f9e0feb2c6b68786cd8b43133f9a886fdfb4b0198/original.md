```
aws_event_stream_message_from_buffer_copy(message, alloc, buffer)
```

Allocates memory and copies buffer. Otherwise the same as aws_aws_event_stream_message_from_buffer. This is slower, but possibly safer.

### Prototype

```c
int aws_event_stream_message_from_buffer_copy( struct aws_event_stream_message *message, struct aws_allocator *alloc, const struct aws_byte_buf *buffer);
```
