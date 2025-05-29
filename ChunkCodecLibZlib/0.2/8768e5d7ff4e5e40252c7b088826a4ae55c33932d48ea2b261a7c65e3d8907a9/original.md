```
struct GzipCodec <: Codec
GzipCodec()
```

gzip compression using libzlib: https://www.zlib.net/

This is the gzip (.gz) format described in RFC 1952

See also [`GzipEncodeOptions`](@ref) and [`GzipDecodeOptions`](@ref)
