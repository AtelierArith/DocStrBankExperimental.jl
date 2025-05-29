```
aws_event_stream_add_uuid_header(headers, name, name_len, value)
```

adds a uuid buffer to the list of headers. Value must always be 16 bytes long.

### Prototype

```c
int aws_event_stream_add_uuid_header( struct aws_array_list *headers, const char *name, uint8_t name_len, const uint8_t *value);
```
