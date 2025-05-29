```
aws_event_stream_header_value_as_timestamp(header)
```

Returns the header value as a 64 bit integer representing milliseconds since unix epoch.

### Prototype

```c
int64_t aws_event_stream_header_value_as_timestamp(struct aws_event_stream_header_value_pair *header);
```
