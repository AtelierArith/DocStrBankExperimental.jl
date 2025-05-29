```
struct DeflateCodec <: Codec
DeflateCodec()
```

libzlibを使用したdeflate圧縮: https://www.zlib.net/

これはRFC 1951で説明されているdeflateフォーマットです

[`DeflateEncodeOptions`](@ref)および[`DeflateDecodeOptions`](@ref)も参照してください
