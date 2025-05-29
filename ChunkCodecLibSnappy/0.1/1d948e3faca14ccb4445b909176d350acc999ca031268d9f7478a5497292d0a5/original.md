```
struct SnappyEncodeOptions <: EncodeOptions
SnappyEncodeOptions(; kwargs...)
```

Snappy compression using the snappy C++ library: https://github.com/google/snappy

The maximum decoded size is about 4 GB.

# Keyword Arguments

  * `codec::SnappyCodec=SnappyCodec()`
