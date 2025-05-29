```
struct BZ2EncodeOptions <: EncodeOptions
BZ2EncodeOptions(; kwargs...)
```

bzip2 compression using libbzip2: https://sourceware.org/bzip2/

# Keyword Arguments

-`codec::BZ2Codec=BZ2Codec()`

  * `blockSize100k::Integer=9`: Specifies the block size to be used for compression.

    It should be a value between 1 and 9 inclusive, and the actual block size used is 100000 x this figure. The default 9 gives the best compression but takes most memory.
