```
aws_tls_alpn_handler_new(allocator, on_protocol_negotiated, user_data)
```

クライアントまたはサーバーモードのためのチャネルハンドラーを作成し、alpnを処理します。これは必ずしも必要ではありません。なぜなら、[`aws_tls_on_negotiation_result_fn`](@ref) コールバック内で常に [`aws_tls_handler_protocol`](@ref) を呼び出すことができるからですが、これによりチャネルのブートストラップがより簡単に処理できます。

### プロトタイプ

```c
struct aws_channel_handler *aws_tls_alpn_handler_new( struct aws_allocator *allocator, aws_tls_on_protocol_negotiated on_protocol_negotiated, void *user_data);
```
