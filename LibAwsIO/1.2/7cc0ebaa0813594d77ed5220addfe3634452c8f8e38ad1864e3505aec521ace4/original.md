```
aws_tls_ctx_acquire(ctx)
```

Increments the reference count on the tls context, allowing the caller to take a reference to it.

Returns the same tls context passed in.

### Prototype

```c
struct aws_tls_ctx *aws_tls_ctx_acquire(struct aws_tls_ctx *ctx);
```
