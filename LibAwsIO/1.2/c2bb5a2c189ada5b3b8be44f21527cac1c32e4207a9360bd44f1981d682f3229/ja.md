```
aws_socket_listen(socket, backlog_size)
```

TCP、LOCAL、および VSOCK のみ。`[`aws*socket*bind`](@ref)()` でバインドされたアドレスでソケットがリッスンするように設定します。

### プロトタイプ

```c
int aws_socket_listen(struct aws_socket *socket, int backlog_size);
```
