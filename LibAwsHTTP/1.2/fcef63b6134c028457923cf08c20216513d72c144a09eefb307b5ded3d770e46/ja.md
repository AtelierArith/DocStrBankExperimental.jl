```
aws_websocket_random_handshake_key(dst)
```

Sec-WebSocket-Key ヘッダーの値を生成し、それを `dst` バッファに書き込みます。バッファには少なくとも [`AWS_WEBSOCKET_MAX_HANDSHAKE_KEY_LENGTH`](@ref) のスペースが必要です。

この値は、ランダムな16バイトの値の base64 エンコーディングです。RFC-6455 セクション 4.1

### プロトタイプ

```c
int aws_websocket_random_handshake_key(struct aws_byte_buf *dst);
```
