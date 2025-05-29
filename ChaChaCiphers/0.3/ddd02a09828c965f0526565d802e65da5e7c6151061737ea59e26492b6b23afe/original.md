```
decrypt(stream::ChaChaStream, x)
decrypt!(stream::ChaChaStream, x)
```

Decrypt an encrypted vector `x` using the keystream from a [`ChaChaStream`](@ref).
