```
struct BloscEncodeOptions <: EncodeOptions
BloscEncodeOptions(; kwargs...)
```

Blosc compression using c-blosc library: https://github.com/Blosc/c-blosc

# Keyword Arguments

  * `codec::BloscCodec=BloscCodec()`
  * `clevel::Integer=5`: The compression level, between 0 (no compression) and 9 (maximum compression)
  * `doshuffle::Integer=1`: Whether to use the shuffle filter.

    0 means not applying it, 1 means applying it at a byte level, and 2 means at a bit level (slower but may achieve better entropy alignment).
  * `typesize::Integer=1`: The element size to use when shuffling.

    For implementation reasons, only `typesize` in `1:255` will allow the shuffle filter to work.  When `typesize` is not in this range, shuffle will be silently disabled.
  * `compressor::AbstractString="lz4"`: The string representing the type of compressor to use.

    For example, "blosclz", "lz4", "lz4hc", "zlib", or "zstd". Use `is_compressor_valid` to check if a compressor is supported.
