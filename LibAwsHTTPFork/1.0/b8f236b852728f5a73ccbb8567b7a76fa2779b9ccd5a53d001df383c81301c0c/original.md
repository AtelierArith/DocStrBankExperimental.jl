```
aws_http_message_add_header_array(message, headers, num_headers)
```

Add an array of headers to the end of the header array. The message makes its own copy of the underlying strings.

This is a helper function useful when it's easier to define headers as a stack array, rather than calling add_header repeatedly.

### Prototype

```c
int aws_http_message_add_header_array( struct aws_http_message *message, const struct aws_http_header *headers, size_t num_headers);
```
