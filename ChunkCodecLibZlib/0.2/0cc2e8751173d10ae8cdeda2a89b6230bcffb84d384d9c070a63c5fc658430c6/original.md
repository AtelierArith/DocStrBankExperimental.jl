```
struct ZlibDecodeOptions <: DecodeOptions
ZlibDecodeOptions(; kwargs...)
```

zlib decompression using libzlib: https://www.zlib.net/

This is the zlib format described in RFC 1950

# Keyword Arguments

  * `codec::ZlibCodec=ZlibCodec()`
