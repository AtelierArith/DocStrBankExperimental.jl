```
aws_event_stream_header_name(header)
```

Returns the header name. Note: this value is not null terminated

### Prototype

```c
struct aws_byte_buf aws_event_stream_header_name( struct aws_event_stream_header_value_pair *header);
```
