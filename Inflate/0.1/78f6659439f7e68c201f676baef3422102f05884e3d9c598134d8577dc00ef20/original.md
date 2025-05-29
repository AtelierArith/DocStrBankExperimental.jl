```
InflateGzipStream(stream::IO)
```

Streaming decompression of Gzip compressed `stream`. For an in-memory counterpart, see `inflate_gzip`.

```
gzip_headers = Dict{String, Any}()
InflateGzipStream(stream::IO; headers = gzip_headers)
```

Also retrieve gzip headers in the provided `Dict`. The headers are available directly after the object is constructed.

```
InflateGzipStream(stream::IO; ignore_checksum = true)
```

Skip computing CRC of the content, as well as the header, for consistency checking.

Reference: [RFC 1952](https://www.ietf.org/rfc/rfc1952.txt)
