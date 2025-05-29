```
struct ZlibEncodeOptions <: EncodeOptions
ZlibEncodeOptions(; kwargs...)
```

zlib compression using libzlib: https://www.zlib.net/

This is the zlib format described in RFC 1950

# Keyword Arguments

  * `codec::ZlibCodec=ZlibCodec()`
  * `level::Integer=-1`: The compression level must be -1, or between 0 and 9.

    1 gives best speed, 9 gives best compression, 0 gives no compression at all (the input data is simply copied a block at a time). -1 requests a default compromise between speed and compression (currently equivalent to level 6).
