```
struct DeflateCodec <: Codec
DeflateCodec()
```

deflate compression using libzlib: https://www.zlib.net/

This is the deflate format described in RFC 1951

See also [`DeflateEncodeOptions`](@ref) and [`DeflateDecodeOptions`](@ref)
