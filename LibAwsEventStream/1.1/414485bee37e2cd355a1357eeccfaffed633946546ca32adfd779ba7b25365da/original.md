```
aws_event_stream_add_int32_header(headers, name, name_len, value)
```

adds a 32 bit integer to the list of headers.

### Prototype

```c
int aws_event_stream_add_int32_header( struct aws_array_list *headers, const char *name, uint8_t name_len, int32_t value);
```
