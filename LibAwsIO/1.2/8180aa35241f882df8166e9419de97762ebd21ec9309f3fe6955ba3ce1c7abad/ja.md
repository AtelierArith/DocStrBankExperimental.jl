```
aws_socket_init(socket, alloc, options)
```

ソケットオブジェクトをソケットオプションで初期化します。optionsはコピーされます。

### プロトタイプ

```c
int aws_socket_init( struct aws_socket *socket, struct aws_allocator *alloc, const struct aws_socket_options *options);
```
