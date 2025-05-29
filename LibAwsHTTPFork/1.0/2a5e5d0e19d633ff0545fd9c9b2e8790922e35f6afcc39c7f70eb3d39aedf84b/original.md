```
aws_http_message_new_websocket_handshake_request(allocator, path, host)
```

Create request with all required fields for a websocket upgrade request. The method and path are set, and the the following headers are added:

Host: <host> Upgrade: websocket Connection: Upgrade Sec-WebSocket-Key: <base64 encoding of 16 random bytes> Sec-WebSocket-Version: 13

### Prototype

```c
struct aws_http_message *aws_http_message_new_websocket_handshake_request( struct aws_allocator *allocator, struct aws_byte_cursor path, struct aws_byte_cursor host);
```
