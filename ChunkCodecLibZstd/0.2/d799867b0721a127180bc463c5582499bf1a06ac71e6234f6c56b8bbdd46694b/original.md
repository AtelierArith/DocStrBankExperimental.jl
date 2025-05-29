```
struct ZstdDecodeOptions <: DecodeOptions
ZstdDecodeOptions(; kwargs...)
```

Zstandard decompression using libzstd: www.zstd.net

Zstandard's format is documented in [RFC8878](https://datatracker.ietf.org/doc/html/rfc8878)

# Keyword Arguments

  * `codec::ZstdCodec=ZstdCodec()`
  * `advanced_parameters::Vector{Pair{Int32, Int32}}=[]`: Pairs of `param => value`.

    Warning, some parameters are experimental and may change in new versions of libzstd, so you may need to check [`ZSTD_versionNumber`](@ref) and [`ZSTD_dParam_getBounds`](@ref). See comments in zstd.h. Additional parameters are set with `ZSTD_DCtx_setParameter`. The vector must not be mutated after calling the constructor.
