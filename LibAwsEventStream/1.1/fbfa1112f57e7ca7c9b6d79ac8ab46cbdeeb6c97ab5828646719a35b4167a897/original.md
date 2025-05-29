```
aws_event_stream_add_int16_header_by_cursor(headers, name, value)
```

Adds a int16-valued header to a header list

# Arguments

  * `headers`: header list to add to
  * `name`: name of the header to add
  * `value`: value of the header to add

# Returns

AWS_OP_SUCCESS on success, AWS_OP_ERR on failure

### Prototype

```c
int aws_event_stream_add_int16_header_by_cursor( struct aws_array_list *headers, struct aws_byte_cursor name, int16_t value);
```
