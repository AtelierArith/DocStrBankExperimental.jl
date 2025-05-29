```
aws_event_stream_header_value_as_bytebuf(header)
```

Returns the header value as a pointer to a byte buffer, call [`aws_event_stream_header_value_length`](@ref) to determine the length of the buffer.

### Prototype

```c
struct aws_byte_buf aws_event_stream_header_value_as_bytebuf( struct aws_event_stream_header_value_pair *header);
```
