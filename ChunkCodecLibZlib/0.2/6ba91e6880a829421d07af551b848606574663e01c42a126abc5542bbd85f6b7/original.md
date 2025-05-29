```
struct DeflateDecodeOptions <: DecodeOptions
DeflateDecodeOptions(; kwargs...)
```

deflate decompression using libzlib: https://www.zlib.net/

This is the deflate format described in RFC 1951

# Keyword Arguments

  * `codec::DeflateCodec=DeflateCodec()`
