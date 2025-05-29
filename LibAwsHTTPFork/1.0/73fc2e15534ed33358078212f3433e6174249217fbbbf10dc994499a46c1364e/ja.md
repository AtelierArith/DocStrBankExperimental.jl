```
aws_http_server_release(server)
```

サーバーを解放します。リスニングソケットとサーバー内のすべての接続が閉じられます。destroy操作が完了すると、on*destroy*completeが呼び出されます。

### プロトタイプ

```c
void aws_http_server_release(struct aws_http_server *server);
```
