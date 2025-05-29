```
aws_http_message_new_websocket_handshake_request(allocator, path, host)
```

WebSocketアップグレードリクエストのために必要なすべてのフィールドを持つリクエストを作成します。メソッドとパスが設定され、次のヘッダーが追加されます：

Host: <host> Upgrade: websocket Connection: Upgrade Sec-WebSocket-Key: <16バイトのランダムなバイトのbase64エンコーディング> Sec-WebSocket-Version: 13

### プロトタイプ

```c
struct aws_http_message *aws_http_message_new_websocket_handshake_request( struct aws_allocator *allocator, struct aws_byte_cursor path, struct aws_byte_cursor host);
```
