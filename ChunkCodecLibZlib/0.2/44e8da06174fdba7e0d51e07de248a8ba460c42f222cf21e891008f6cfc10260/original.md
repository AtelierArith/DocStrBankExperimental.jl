```
struct DeflateEncodeOptions <: EncodeOptions
DeflateEncodeOptions(; kwargs...)
```

deflate compression using libzlib: https://www.zlib.net/

This is the deflate format described in RFC 1951

# Keyword Arguments

  * `codec::DeflateCodec=DeflateCodec()`
  * `level::Integer=-1`: The compression level must be -1, or between 0 and 9.

    1 gives best speed, 9 gives best compression, 0 gives no compression at all (the input data is simply copied a block at a time). -1 requests a default compromise between speed and compression (currently equivalent to level 6).
