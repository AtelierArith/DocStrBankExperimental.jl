```
aws_socket_subscribe_to_readable_events(socket, on_readable, user_data)
```

ソケットが読み取り可能になるときに通知を受け取るために on_readable を購読します（エッジトリガー）。エラーもコールバックで受け取ります。

注意！この関数は技術的にはスレッドセーフではありませんが、どのスレッドから呼び出すかは強制しません。安全に呼び出すか（例えば、複数のスレッドから並行して呼び出さないなど）か、呼び出すタスクをスケジュールする責任はあなたにあります。最初の読み取り呼び出しの前に呼び出しても問題ありません。

### プロトタイプ

```c
int aws_socket_subscribe_to_readable_events( struct aws_socket *socket, aws_socket_on_readable_fn *on_readable, void *user_data);
```
