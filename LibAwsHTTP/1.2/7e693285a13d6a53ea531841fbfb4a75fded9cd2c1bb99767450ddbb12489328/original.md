```
aws_http_message_set_body_stream(message, body_stream)
```

Set the body stream. NULL is an acceptable value for messages with no body. Note: The message does NOT take ownership of the body stream. The stream must not be destroyed until the message is complete.

### Prototype

```c
void aws_http_message_set_body_stream(struct aws_http_message *message, struct aws_input_stream *body_stream);
```
