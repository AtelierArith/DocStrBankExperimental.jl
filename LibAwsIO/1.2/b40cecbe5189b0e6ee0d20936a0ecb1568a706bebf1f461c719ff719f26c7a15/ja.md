```
aws_socket_get_error(socket)
```

ソケットから最新のエラーを取得します。エラーが発生していない場合は、AWS*OP*SUCCESSが返されます。この関数は、インストールされたエラーハンドラーにエラーを発生させません。

### プロトタイプ

```c
int aws_socket_get_error(struct aws_socket *socket);
```
