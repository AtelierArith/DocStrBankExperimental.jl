```
struct SnappyDecodeOptions <: DecodeOptions
SnappyDecodeOptions(; kwargs...)
```

Snappyデコーディングは、snappy C++ライブラリを使用します: https://github.com/google/snappy

# キーワード引数

  * `codec::SnappyCodec=SnappyCodec()`
