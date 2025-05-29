```
aws_http_message_get_header(message, out_header, index)
```

Get the header at the specified index. This function cannot fail if a valid index is provided. Otherwise, AWS_ERROR_INVALID_INDEX will be raised.

The underlying strings are stored within the message.

### Prototype

```c
int aws_http_message_get_header( const struct aws_http_message *message, struct aws_http_header *out_header, size_t index);
```
