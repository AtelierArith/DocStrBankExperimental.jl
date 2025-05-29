```
aws_socket_connect(socket, socket_connect_options)
```

リモートエンドポイントに接続します。UDPでは、これは単にソケットをリモートアドレスにバインドして `[`aws*socket*write`](@ref)()` で使用するためのものであり、操作が成功した場合、ソケットはすぐに書き込み操作に使用できます。

TCP、LOCAL、および VSOCK では、この関数はブロックしません。戻り値が成功した場合、ソケットを使用する前に `on\_connection\_result()` コールバックが呼び出されるのを待つ必要があります。

UDPソケットに対して event*loop が提供されている場合、event-loop のスレッドで on*connection*result に通知が送信されます。完了すると、ソケットにはすでにイベントループが割り当てられます。UDP に NULL が渡された場合、成功するとすぐに戻りますが、使用する前に [`aws*socket*assign*to*event*loop`](@ref) を呼び出す必要があります。

### プロトタイプ

```c
int aws_socket_connect(struct aws_socket *socket, struct aws_socket_connect_options *socket_connect_options);
```
