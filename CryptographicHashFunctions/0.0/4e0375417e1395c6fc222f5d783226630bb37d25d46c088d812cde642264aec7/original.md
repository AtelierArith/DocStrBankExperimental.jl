```
digest!(obj)
```

Return the digest for the HMAC object or hash context `obj` of a hash algorithm.

Unless `reset!` is called before, further calls to `update!` or `digest!` are not allowed.

```
digest!(ctx, len)
```

Return the next `len` bytes of the digest for the hash context `ctx` of an XOF algorithm.

Unless `reset!` is called before, further calls to `update!` are not allowed. If the provider does not support streaming, further calls to `digest!` are forbidden, too.
