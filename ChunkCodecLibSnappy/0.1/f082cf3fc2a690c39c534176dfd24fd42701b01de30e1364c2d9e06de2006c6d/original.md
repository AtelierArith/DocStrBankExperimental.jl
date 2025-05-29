```
struct SnappyDecodeOptions <: DecodeOptions
SnappyDecodeOptions(; kwargs...)
```

Snappy decompression using the snappy C++ library: https://github.com/google/snappy

# Keyword Arguments

  * `codec::SnappyCodec=SnappyCodec()`
