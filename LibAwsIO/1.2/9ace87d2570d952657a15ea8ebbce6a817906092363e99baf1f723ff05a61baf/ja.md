```
aws_tls_server_ctx_new(alloc, options)
```

新しいサーバーコンテキストを作成します。このコンテキストは、すべての受信接続に対して同じオプションを使用することを想定して、アプリケーションのライフタイム中に使用できます。オプションはコピーされます。

### プロトタイプ

```c
struct aws_tls_ctx *aws_tls_server_ctx_new( struct aws_allocator *alloc, const struct aws_tls_ctx_options *options);
```
