```
encrypt(stream::ChaChaStream, x)
encrypt!(stream::ChaChaStream, x)
```

Encrypt a vector or string `x` using the keystream from a [`ChaChaStream`](@ref).
