```
aws_socket_is_open(socket)
```

ソケットがまだオープンである場合はtrueを返します（接続されているまたはリスニングしていることを意味するのではなく、単にclose()が呼ばれていないことを意味します）。

### プロトタイプ

```c
bool aws_socket_is_open(struct aws_socket *socket);
```
