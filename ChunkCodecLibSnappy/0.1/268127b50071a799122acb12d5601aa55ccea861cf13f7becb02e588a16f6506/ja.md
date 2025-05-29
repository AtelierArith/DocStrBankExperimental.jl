```
struct SnappyCodec <: Codec
SnappyCodec()
```

Snappy圧縮は、snappy C++ライブラリを使用しています: https://github.com/google/snappy

最大デコードサイズは約4 GBです。

[`SnappyEncodeOptions`](@ref)および[`SnappyDecodeOptions`](@ref)も参照してください。
