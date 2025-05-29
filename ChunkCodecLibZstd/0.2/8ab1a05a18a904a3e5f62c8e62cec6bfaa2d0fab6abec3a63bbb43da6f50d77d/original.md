```
struct ZstdCodec <: Codec
ZstdCodec()
```

Zstandard compression using libzstd: www.zstd.net

Zstandard's format is documented in [RFC8878](https://datatracker.ietf.org/doc/html/rfc8878)

Like libzstd's simple API, encode compresses data as a single frame with saved decompressed size. Decoding will succeed even if the decompressed size is unknown. Also like libzstd's simple API, decoding accepts concatenated frames  and will error if there is invalid data appended.

See also [`ZstdEncodeOptions`](@ref) and [`ZstdDecodeOptions`](@ref)
