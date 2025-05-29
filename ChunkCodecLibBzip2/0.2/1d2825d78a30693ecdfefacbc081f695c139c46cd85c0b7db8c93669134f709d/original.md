```
struct BZ2DecodeOptions <: DecodeOptions
BZ2DecodeOptions(; kwargs...)
```

bzip2 decompression using libbzip2: https://sourceware.org/bzip2/

Like the command line tool `bunzip2`, decoding accepts concatenated compressed data and returns the decompressed data concatenated. Unlike `bunzip2`, decoding will error if the compressed stream has invalid data appended to it.

# Keyword Arguments

  * `codec::BZ2Codec=BZ2Codec()`
