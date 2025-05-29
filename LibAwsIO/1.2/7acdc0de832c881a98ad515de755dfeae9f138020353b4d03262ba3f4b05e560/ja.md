```
aws_server_bootstrap_destroy_socket_listener(bootstrap, listener)
```

'listener'をシャットダウンし、それに関連するリソースをクリーンアップします。`listener`上のすべての受信チャネルはまだアクティブです。サーバーソケットリスナーが破棄された後、すべての関連接続とチャネルがシャットダウンを完了した後に`destroy_callback`が呼び出されます。

### プロトタイプ

```c
void aws_server_bootstrap_destroy_socket_listener( struct aws_server_bootstrap *bootstrap, struct aws_socket *listener);
```
