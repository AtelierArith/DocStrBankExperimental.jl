```
aws_http_server_get_listener_endpoint(server)
```

HTTPサーバーのローカルリスナーエンドポイントを返します。サーバーが有効である限りのみ有効です。

### プロトタイプ

```c
const struct aws_socket_endpoint *aws_http_server_get_listener_endpoint(const struct aws_http_server *server);
```
