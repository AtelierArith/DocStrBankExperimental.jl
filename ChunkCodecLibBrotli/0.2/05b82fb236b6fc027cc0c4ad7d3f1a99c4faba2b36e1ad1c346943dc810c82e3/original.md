```
struct BrotliEncodeOptions <: EncodeOptions
BrotliEncodeOptions(; kwargs...)
```

brotli compression using the brotli C library [https://brotli.org/](https://brotli.org/)

This is the brotli (.br) format described in RFC 7932

# Keyword Arguments

  * `codec::BrotliCodec=BrotliCodec()`
  * `quality::Integer=11`: The quality must be between 0 and 11.

    0 gives best compression speed, 11 gives best compressed size.
  * `lgwin::Integer=24`: Sliding LZ77 window size is at most `(1 << lgwin) - 16`.

    Must be between 10 and 24. Encoder may reduce this value, e.g. if input is much smaller than window size.
  * `mode::Integer=0`: Tune encoder for specific input.

    0 is default. 1 is for UTF-8 text. 2 is for WOFF 2.0.
