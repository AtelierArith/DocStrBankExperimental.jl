```
aws_event_stream_header_value_length(header)
```

Returns the length of the header value buffer. This is mostly intended for string and byte buffer types.

### Prototype

```c
uint16_t aws_event_stream_header_value_length(struct aws_event_stream_header_value_pair *header);
```
