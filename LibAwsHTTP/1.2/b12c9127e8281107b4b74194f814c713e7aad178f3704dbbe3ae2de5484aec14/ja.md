```
aws_websocket_client_connect(options)
```

非同期的にクライアントウェブソケット接続を確立します。on*connection*setupコールバックは、操作が接続の作成を完了したとき、または失敗したときに呼び出されます。

### プロトタイプ

```c
int aws_websocket_client_connect(const struct aws_websocket_client_connection_options *options);
```
