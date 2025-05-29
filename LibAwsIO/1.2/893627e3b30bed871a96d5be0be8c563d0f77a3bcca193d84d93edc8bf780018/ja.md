```
aws_socket_assign_to_event_loop(socket, event_loop)
```

ソケットをイベントループに割り当てます。この呼び出しの後、ソケットは読み取り/書き込み/エラー通知を受け始めます。

注意: TCPまたはUnixドメインソケットのためにconnectを呼び出し、connection_successコールバックを受け取った場合、これはすでに発生しています。この関数を呼び出す必要があるのは次の場合です：

a.) このソケットがサーバーソケットである場合（例: start_accept()の呼び出しの結果） b.) このソケットがUDPソケットである場合。

### プロトタイプ

```c
int aws_socket_assign_to_event_loop(struct aws_socket *socket, struct aws_event_loop *event_loop);
```
