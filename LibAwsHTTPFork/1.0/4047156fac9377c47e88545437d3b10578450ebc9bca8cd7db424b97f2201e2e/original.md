```
aws_http_message_erase_header(message, index)
```

Remove the header at the specified index. Headers after this index are all shifted back one position.

This function cannot fail if a valid index is provided. Otherwise, AWS_ERROR_INVALID_INDEX will be raised.

### Prototype

```c
int aws_http_message_erase_header(struct aws_http_message *message, size_t index);
```
