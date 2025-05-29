```
struct GzipDecodeOptions <: DecodeOptions
GzipDecodeOptions(; kwargs...)
```

gzip decompression using libzlib: https://www.zlib.net/

This is the gzip (.gz) format described in RFC 1952

# Keyword Arguments

  * `codec::GzipCodec=GzipCodec()`
