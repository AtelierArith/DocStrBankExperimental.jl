```
aws_tls_ctx_release(ctx)
```

Decrements a tls context's ref count. When the ref count drops to zero, the object will be destroyed.

### Prototype

```c
void aws_tls_ctx_release(struct aws_tls_ctx *ctx);
```
