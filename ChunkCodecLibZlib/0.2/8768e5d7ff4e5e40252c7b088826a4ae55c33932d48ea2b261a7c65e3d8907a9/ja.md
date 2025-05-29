```
struct GzipCodec <: Codec
GzipCodec()
```

libzlibを使用したgzip圧縮: https://www.zlib.net/

これはRFC 1952で説明されているgzip (.gz)フォーマットです

[`GzipEncodeOptions`](@ref)および[`GzipDecodeOptions`](@ref)も参照してください
