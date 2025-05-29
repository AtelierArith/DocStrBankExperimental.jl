```
aws_event_stream_message_init(message, alloc, headers, payload)
```

Initializes with a list of headers, the payload, and a payload length. CRCs will be computed for you. If headers or payload is NULL, then the fields will be appropriately set to indicate no headers and/or no payload. Both payload and headers will result in an allocation.

### Prototype

```c
int aws_event_stream_message_init( struct aws_event_stream_message *message, struct aws_allocator *alloc, const struct aws_array_list *headers, const struct aws_byte_buf *payload);
```
