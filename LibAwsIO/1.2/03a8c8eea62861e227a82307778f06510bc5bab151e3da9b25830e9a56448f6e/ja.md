```
aws_tls_client_handler_start_negotiation(handler)
```

交渉プロセスを開始します。この関数は、TLSハンドシェイクを開始するためにクライアントモードのときに呼び出す必要があります。ハンドシェイクが完了すると、[`aws_tls_on_negotiation_result_fn`](@ref) が呼び出されます。

### プロトタイプ

```c
int aws_tls_client_handler_start_negotiation(struct aws_channel_handler *handler);
```
