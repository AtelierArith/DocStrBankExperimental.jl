```
struct BZ2Codec <: Codec
BZ2Codec()
```

bzip2 compression using libbzip2: https://sourceware.org/bzip2/

Like the command line tool `bunzip2`, decoding accepts concatenated compressed data and returns the decompressed data concatenated. Unlike `bunzip2`, decoding will error if the compressed stream has invalid data appended to it.

See also [`BZ2EncodeOptions`](@ref) and [`BZ2DecodeOptions`](@ref)
