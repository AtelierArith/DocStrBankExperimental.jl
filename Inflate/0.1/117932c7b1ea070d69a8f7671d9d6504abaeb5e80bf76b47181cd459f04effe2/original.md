```
inflate_gzip(source::Vector{UInt8})
```

Decompress in-memory `source`, in Gzip compressed format. The output will also be a `Vector{UInt8}`. For a streaming counterpart, see `InflateGzipStream`.

```
gzip_headers = Dict{String, Any}()
inflate_gzip(source::Vector{UInt8}; headers = gzip_headers)
```

Also retrieve gzip headers in the provided `Dict`.

```
inflate_gzip(source::Vector{UInt8}; ignore_checksum = true)
```

Skip computing CRC of the content, as well as the header, for consistency checking.

Reference: [RFC 1952](https://www.ietf.org/rfc/rfc1952.txt)
