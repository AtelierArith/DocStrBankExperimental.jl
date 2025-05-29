```
update!(obj, data[; provider, kwargs...])
```

Feed `data` into the hash context or HMAC object `obj`.

The argument `data` can be of type `AbstractVector{UInt8}`, `AbstractString`, `IO`, or any other type that can be collected into a vector of bytes.

When reading `data` of type `IO`, the buffer size can be set with the optional keyword argument `buffersize`.
