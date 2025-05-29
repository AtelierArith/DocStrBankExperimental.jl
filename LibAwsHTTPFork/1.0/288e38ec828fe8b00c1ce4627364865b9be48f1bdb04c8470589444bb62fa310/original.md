```
aws_http_message_new_websocket_handshake_response(allocator, accept_key)
```

Create response with all required fields for a websocket upgrade response. The following headers are added:

Upgrade: websocket Connection: Upgrade Sec-WebSocket-Accept: <base64 encoded accept key>

### Prototype

```c
struct aws_http_message *aws_http_message_new_websocket_handshake_response( struct aws_allocator *allocator, struct aws_byte_cursor accept_key);
```
