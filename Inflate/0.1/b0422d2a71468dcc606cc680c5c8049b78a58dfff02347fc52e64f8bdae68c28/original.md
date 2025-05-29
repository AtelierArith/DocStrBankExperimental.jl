```
inflate_zlib(source::Vector{UInt8})
```

Decompress in-memory `source`, in Zlib compressed format. The output will also be a `Vector{UInt8}`. For a streaming counterpart, see `InflateZlibStream`.

```
inflate_zlib(source::Vector{UInt8}; ignore_checksum = true)
```

Skip computing Adler checksum for consistency checking.

Reference: [RFC 1950](https://www.ietf.org/rfc/rfc1950.txt)
