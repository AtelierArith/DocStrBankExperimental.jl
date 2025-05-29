```
aws_socket_shutdown_dir(socket, dir)
```

ソケットの方向に基づいて `shutdown()` を呼び出します。

### プロトタイプ

```c
int aws_socket_shutdown_dir(struct aws_socket *socket, enum aws_channel_direction dir);
```
