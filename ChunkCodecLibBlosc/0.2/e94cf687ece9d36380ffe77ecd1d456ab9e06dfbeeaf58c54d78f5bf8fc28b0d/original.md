```
struct BloscDecodeOptions <: DecodeOptions
BloscDecodeOptions(; kwargs...)
```

Blosc decompression using c-blosc library: https://github.com/Blosc/c-blosc

# Keyword Arguments

  * `codec::BloscCodec=BloscCodec()`
