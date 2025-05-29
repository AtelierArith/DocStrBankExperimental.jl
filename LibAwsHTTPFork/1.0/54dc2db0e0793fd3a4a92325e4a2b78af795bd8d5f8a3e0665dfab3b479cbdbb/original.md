```
aws_http_message_add_header(message, header)
```

Add a header to the end of the array. The message makes its own copy of the underlying strings.

### Prototype

```c
int aws_http_message_add_header(struct aws_http_message *message, struct aws_http_header header);
```
