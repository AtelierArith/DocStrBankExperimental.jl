```
CuContext(pctx::CuPrimaryContext)
```

Derive a context from a primary context.

Calling this function increases the reference count of the primary context. The returned context *should not* be free with the `unsafe_destroy!` function that's used with ordinary contexts. Instead, the refcount of the primary context should be decreased by calling `unsafe_release!`, or set to zero by calling `unsafe_reset!`. The easiest way to do this is by using the `do`-block syntax.
