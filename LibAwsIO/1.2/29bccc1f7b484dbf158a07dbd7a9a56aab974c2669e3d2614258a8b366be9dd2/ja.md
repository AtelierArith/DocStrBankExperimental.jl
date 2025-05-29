```
aws_socket_set_close_complete_callback(socket, fn, user_data)
```

Apple Network Framework のみ。[`aws_socket_close`](@ref)() が完了したときにトリガーされるコールバック。コールバックはソケットイベントループから呼び出されます。

### プロトタイプ

```c
int aws_socket_set_close_complete_callback( struct aws_socket *socket, aws_socket_on_shutdown_complete_fn fn, void *user_data);
```
