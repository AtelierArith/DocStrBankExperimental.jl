```
struct BrotliCodec <: Codec
BrotliCodec()
```

brotli compression using the brotli C library [https://brotli.org/](https://brotli.org/)

This is the brotli (.br) format described in RFC 7932

See also [`BrotliEncodeOptions`](@ref) and [`BrotliDecodeOptions`](@ref)
