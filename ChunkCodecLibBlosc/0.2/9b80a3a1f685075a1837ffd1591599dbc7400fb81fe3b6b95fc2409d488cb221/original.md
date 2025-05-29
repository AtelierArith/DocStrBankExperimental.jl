```
struct BloscCodec <: Codec
BloscCodec()
```

Blosc compression using c-blosc library: https://github.com/Blosc/c-blosc

Decoding does not accept any extra data appended to the compressed block. Decoding also does not accept truncated data, or multiple compressed blocks concatenated together.

[`BloscEncodeOptions`](@ref) and [`BloscDecodeOptions`](@ref) can be used to set decoding and encoding options.
