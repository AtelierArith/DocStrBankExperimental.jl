```
aws_socket_start_accept(socket, accept_loop, options)
```

TCP、LOCAL、および VSOCK のみ。ソケットは新しい接続を受け入れ始めます。これは非同期操作です。新しい接続やエラーは `on_accept_result` コールバックを介して到着します。

[`aws_socket_bind`](@ref)() および [`aws_socket_listen`](@ref)() は、この関数を呼び出す前に呼び出す必要があります。

### プロトタイプ

```c
int aws_socket_start_accept( struct aws_socket *socket, struct aws_event_loop *accept_loop, struct aws_socket_listener_options options);
```
