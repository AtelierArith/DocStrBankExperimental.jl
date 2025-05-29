```
struct SnappyCodec <: Codec
SnappyCodec()
```

Snappy compression using the snappy C++ library: https://github.com/google/snappy

The maximum decoded size is about 4 GB.

See also [`SnappyEncodeOptions`](@ref) and [`SnappyDecodeOptions`](@ref)
