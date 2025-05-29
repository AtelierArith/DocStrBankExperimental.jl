```
aws_http_message_set_request_path(request_message, path)
```

Set the path-and-query value (request messages only). The request makes its own copy of the underlying string.

### Prototype

```c
int aws_http_message_set_request_path(struct aws_http_message *request_message, struct aws_byte_cursor path);
```
