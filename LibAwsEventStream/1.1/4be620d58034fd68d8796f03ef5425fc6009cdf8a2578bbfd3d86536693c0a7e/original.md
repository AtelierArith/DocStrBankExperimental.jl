```
aws_event_stream_add_bool_header(headers, name, name_len, value)
```

Adds a bool header to the list of headers.

### Prototype

```c
int aws_event_stream_add_bool_header( struct aws_array_list *headers, const char *name, uint8_t name_len, int8_t value);
```
