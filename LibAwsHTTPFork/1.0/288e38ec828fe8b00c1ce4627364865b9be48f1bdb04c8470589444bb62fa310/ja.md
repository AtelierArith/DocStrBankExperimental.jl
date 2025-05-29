```
aws_http_message_new_websocket_handshake_response(allocator, accept_key)
```

WebSocketアップグレードレスポンスのために必要なすべてのフィールドを持つレスポンスを作成します。次のヘッダーが追加されます：

Upgrade: websocket Connection: Upgrade Sec-WebSocket-Accept: <base64エンコードされたアクセプトキー>

### プロトタイプ

```c
struct aws_http_message *aws_http_message_new_websocket_handshake_response( struct aws_allocator *allocator, struct aws_byte_cursor accept_key);
```
