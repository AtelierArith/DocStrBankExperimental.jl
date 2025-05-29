```
aws_event_stream_header_value_as_uuid(header)
```

Returns the header value a byte buffer which is 16 bytes long. Represents a UUID.

### Prototype

```c
struct aws_byte_buf aws_event_stream_header_value_as_uuid( struct aws_event_stream_header_value_pair *header);
```
