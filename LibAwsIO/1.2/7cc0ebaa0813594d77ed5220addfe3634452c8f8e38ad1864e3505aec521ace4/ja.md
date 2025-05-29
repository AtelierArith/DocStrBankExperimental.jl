```
aws_tls_ctx_acquire(ctx)
```

tls コンテキストの参照カウントを増加させ、呼び出し元がそれを参照できるようにします。

渡されたのと同じ tls コンテキストを返します。

### プロトタイプ

```c
struct aws_tls_ctx *aws_tls_ctx_acquire(struct aws_tls_ctx *ctx);
```
