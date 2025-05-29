```
aws_websocket_is_websocket_request(request)
```

リクエストが有効なウェブソケットアップグレードリクエストである場合はtrueを返します。

### プロトタイプ

```c
bool aws_websocket_is_websocket_request(const struct aws_http_message *request);
```
