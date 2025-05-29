```
aws_tls_handler_protocol(handler)
```

Returns a byte buffer by copy of the negotiated protocols. If there is no agreed upon protocol, len will be 0 and buffer will be NULL.

### Prototype

```c
struct aws_byte_buf aws_tls_handler_protocol(struct aws_channel_handler *handler);
```
