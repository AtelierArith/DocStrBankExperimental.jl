```
struct ZstdEncodeOptions <: EncodeOptions
ZstdEncodeOptions(; kwargs...)
```

Zstandard compression using libzstd: www.zstd.net

Zstandard's format is documented in [RFC8878](https://datatracker.ietf.org/doc/html/rfc8878)

# Keyword Arguments

  * `codec::ZstdCodec=ZstdCodec()`
  * `compressionLevel::Integer=0`: Compression level, regular levels are 1-22.

    Levels ≥ 20 should be used with caution, as they require more memory. The library also offers negative compression levels, which extend the range of speed vs. ratio preferences. The lower the level, the faster the speed (at the cost of compression). 0 is a special value for `ZSTD_defaultCLevel()`. The level will be clamped to the range `ZSTD_minCLevel()` to `ZSTD_maxCLevel()`.
  * `checksum::Bool=false`: A 32-bits checksum of content is written at end of frame.
  * `advanced_parameters::Vector{Pair{Int32, Int32}}=[]`: Pairs of `param => value`.

    Warning, some parameters can result in encodings that are incompatible with default decoders. Some parameters are experimental and may change in new versions of libzstd, so you may need to check [`ZSTD_versionNumber`](@ref) and [`ZSTD_cParam_getBounds`](@ref). See comments in zstd.h. Additional parameters are set with `ZSTD_CCtx_setParameter`. These parameters are set after the compression level, and checksum options are set,  so they can override those values. The vector must not be mutated after calling the constructor.
