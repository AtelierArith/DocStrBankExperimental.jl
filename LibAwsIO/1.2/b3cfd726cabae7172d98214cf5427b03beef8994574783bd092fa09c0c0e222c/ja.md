```
aws_socket_stop_accept(socket)
```

TCP、LOCAL、および VSOCK のみ。リスニングソケットは新しい接続の受け入れを停止します。この操作の後に `[`aws*socket*start_accept`](@ref)()` を再度呼び出すことは安全です。これは任意のスレッドから呼び出すことができますが、一部のプラットフォームでは、現在のイベントループのスレッドの外からこれを呼び出すと、イベントループが自身のスレッドでの解除リクエストの処理を完了するまでブロックされることに注意してください。

### プロトタイプ

```c
int aws_socket_stop_accept(struct aws_socket *socket);
```
