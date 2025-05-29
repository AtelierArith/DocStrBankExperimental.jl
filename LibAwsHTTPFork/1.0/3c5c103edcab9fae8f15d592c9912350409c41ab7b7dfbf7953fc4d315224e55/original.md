```
aws_http_message_set_request_method(request_message, method)
```

Set the method (request messages only). The request makes its own copy of the underlying string.

### Prototype

```c
int aws_http_message_set_request_method(struct aws_http_message *request_message, struct aws_byte_cursor method);
```
