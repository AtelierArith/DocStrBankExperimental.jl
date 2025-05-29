```
struct SnappyEncodeOptions <: EncodeOptions
SnappyEncodeOptions(; kwargs...)
```

Snappy圧縮は、snappy C++ライブラリを使用しています: https://github.com/google/snappy

最大デコードサイズは約4 GBです。

# キーワード引数

  * `codec::SnappyCodec=SnappyCodec()`
