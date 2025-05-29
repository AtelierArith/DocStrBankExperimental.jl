```
aws_tls_client_ctx_new(alloc, options)
```

新しいクライアントコンテキストを作成します。このコンテキストは、すべての送信接続に対して同じオプションを使用することを前提として、アプリケーションのライフタイム中に使用できます。オプションはコピーされます。

### プロトタイプ

```c
struct aws_tls_ctx *aws_tls_client_ctx_new( struct aws_allocator *alloc, const struct aws_tls_ctx_options *options);
```
