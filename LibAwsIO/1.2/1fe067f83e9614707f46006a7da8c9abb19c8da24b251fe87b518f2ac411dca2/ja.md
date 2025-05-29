```
aws_socket_bind(socket, socket_bind_options)
```

ソケットをローカルアドレスにバインドします。UDPモードでは、ソケットは `[`aws*socket*read`](@ref)()` 操作の準備が整います。接続指向モードでは、ソケットを使用する前に `[`aws*socket*listen`](@ref)()` と `[`aws*socket*start*accept`](@ref)()` を呼び出す必要があります。local*endpointはコピーされます。

### プロトタイプ

```c
int aws_socket_bind(struct aws_socket *socket, struct aws_socket_bind_options *socket_bind_options);
```
