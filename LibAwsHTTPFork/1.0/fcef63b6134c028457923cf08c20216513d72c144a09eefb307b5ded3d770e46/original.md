```
aws_websocket_random_handshake_key(dst)
```

Generate value for a Sec-WebSocket-Key header and write it into `dst` buffer. The buffer should have at least [`AWS_WEBSOCKET_MAX_HANDSHAKE_KEY_LENGTH`](@ref) space available.

This value is the base64 encoding of a random 16-byte value. RFC-6455 Section 4.1

### Prototype

```c
int aws_websocket_random_handshake_key(struct aws_byte_buf *dst);
```
