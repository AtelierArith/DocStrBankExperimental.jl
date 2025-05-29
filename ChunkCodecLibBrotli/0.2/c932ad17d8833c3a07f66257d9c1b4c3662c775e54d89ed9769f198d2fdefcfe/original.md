```
struct BrotliDecodeOptions <: DecodeOptions
BrotliDecodeOptions(; kwargs...)
```

brotli decompression using the brotli C library [https://brotli.org/](https://brotli.org/)

This is the brotli (.br) format described in RFC 7932

# Keyword Arguments

  * `codec::BrotliCodec=BrotliCodec()`
