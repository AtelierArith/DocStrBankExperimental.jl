```
aws_socket_set_cleanup_complete_callback(socket, fn, user_data)
```

Apple Network Framework のみ。aws*socket*cleanup() が完了したときにトリガーされるコールバックです。その後にソケットを解放するのが安全です。コールバックはソケットイベントループから呼び出されます。

### プロトタイプ

```c
int aws_socket_set_cleanup_complete_callback( struct aws_socket *socket, aws_socket_on_shutdown_complete_fn fn, void *user_data);
```
