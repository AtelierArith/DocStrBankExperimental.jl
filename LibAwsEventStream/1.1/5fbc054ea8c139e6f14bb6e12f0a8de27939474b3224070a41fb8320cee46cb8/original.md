```
aws_event_stream_header_value_as_string(header)
```

Returns the header value as a string. Note: this value is not null terminated.

### Prototype

```c
struct aws_byte_buf aws_event_stream_header_value_as_string( struct aws_event_stream_header_value_pair *header);
```
