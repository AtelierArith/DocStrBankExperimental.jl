```
aws_event_stream_message_from_buffer(message, alloc, buffer)
```

Zero allocation, Zero copy. The message will simply wrap the buffer. The message functions are only useful as long as buffer is referencable memory.

### Prototype

```c
int aws_event_stream_message_from_buffer( struct aws_event_stream_message *message, struct aws_allocator *alloc, struct aws_byte_buf *buffer);
```
