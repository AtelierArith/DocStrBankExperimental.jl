```
aws_socket_get_bound_address(socket, out_address)
```

ソケットがバインドされているローカルアドレスを取得します。アドレスがバインドされていない場合はエラーを発生させます。

### プロトタイプ

```c
int aws_socket_get_bound_address(const struct aws_socket *socket, struct aws_socket_endpoint *out_address);
```
