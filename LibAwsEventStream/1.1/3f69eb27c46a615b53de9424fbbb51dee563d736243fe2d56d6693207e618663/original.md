```
aws_event_stream_add_timestamp_header(headers, name, name_len, value)
```

adds a 64 bit integer representing milliseconds since unix epoch to the list of headers.

### Prototype

```c
int aws_event_stream_add_timestamp_header( struct aws_array_list *headers, const char *name, uint8_t name_len, int64_t value);
```
