```
aws_event_stream_add_bytebuf_header(headers, name, name_len, value, value_len, copy)
```

Adds a byte-buffer header to the list of headers. If copy is set to true, this will result in an allocation for the header value. Otherwise, the value will be set to the memory address of 'value'.

### Prototype

```c
int aws_event_stream_add_bytebuf_header( struct aws_array_list *headers, const char *name, uint8_t name_len, uint8_t *value, uint16_t value_len, int8_t copy);
```
