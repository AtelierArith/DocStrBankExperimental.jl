```
aws_tls_ctx_release(ctx)
```

tls コンテキストの参照カウントを減少させます。参照カウントがゼロになると、オブジェクトは破棄されます。

### プロトタイプ

```c
void aws_tls_ctx_release(struct aws_tls_ctx *ctx);
```
