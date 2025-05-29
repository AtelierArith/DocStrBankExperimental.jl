```
aws_http_message_get_body_stream(message)
```

Get the body stream. Returns NULL if no body stream is set.

### Prototype

```c
struct aws_input_stream *aws_http_message_get_body_stream(const struct aws_http_message *message);
```
