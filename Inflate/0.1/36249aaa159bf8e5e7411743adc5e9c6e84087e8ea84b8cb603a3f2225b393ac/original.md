```
inflate(source::Vector{UInt8})
```

Decompress in-memory `source`, in unwrapped deflate format. The output will also be a `Vector{UInt8}`. For a streaming counterpart, see `InflateStream`.

Reference: [RFC 1951](https://www.ietf.org/rfc/rfc1951.txt)
