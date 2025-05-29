```
struct DeflateDecodeOptions <: DecodeOptions
DeflateDecodeOptions(; kwargs...)
```

libzlibを使用したdeflateデコーディング: https://www.zlib.net/

これはRFC 1951で説明されているdeflateフォーマットです

# キーワード引数

  * `codec::DeflateCodec=DeflateCodec()`
