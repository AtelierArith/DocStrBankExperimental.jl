```
InflateZlibStream(stream::IO)
```

Streaming decompression of Zlib compressed `stream`. For an in-memory counterpart, see `inflate_zlib`.

```
InflateZlibStream(stream::IO; ignore_checksum = true)
```

Skip computing Adler checksum for consistency checking.

Reference: [RFC 1950](https://www.ietf.org/rfc/rfc1950.txt)
