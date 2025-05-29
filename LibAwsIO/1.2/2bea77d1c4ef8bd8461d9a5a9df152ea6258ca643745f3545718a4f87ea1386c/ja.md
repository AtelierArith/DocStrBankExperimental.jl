```
aws_tls_client_handler_new(allocator, options, slot)
```

クライアントモードで新しいtlsチャネルハンドラーを作成します。オプションはコピーされます。ハンドラーがアプリケーションデータの処理を開始する前に、[`aws_tls_client_handler_start_negotiation`](@ref)を呼び出し、[`aws_tls_on_negotiation_result_fn`](@ref)コールバックで待機する必要があります。

### プロトタイプ

```c
struct aws_channel_handler *aws_tls_client_handler_new( struct aws_allocator *allocator, struct aws_tls_connection_options *options, struct aws_channel_slot *slot);
```
