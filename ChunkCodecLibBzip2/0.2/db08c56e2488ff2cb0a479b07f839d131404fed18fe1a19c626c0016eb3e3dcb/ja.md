```
struct BZ2EncodeOptions <: EncodeOptions
BZ2EncodeOptions(; kwargs...)
```

bzip2 圧縮は libbzip2 を使用します: https://sourceware.org/bzip2/

# キーワード引数

-`codec::BZ2Codec=BZ2Codec()`

  * `blockSize100k::Integer=9`: 圧縮に使用されるブロックサイズを指定します。

    これは 1 から 9 までの値でなければならず、実際に使用されるブロックサイズはこの数値の 100000 倍です。デフォルトの 9 は最も良い圧縮を提供しますが、最も多くのメモリを消費します。
