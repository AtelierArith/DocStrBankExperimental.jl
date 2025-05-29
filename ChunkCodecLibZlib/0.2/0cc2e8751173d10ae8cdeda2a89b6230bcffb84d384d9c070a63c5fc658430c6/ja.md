```
struct ZlibDecodeOptions <: DecodeOptions
ZlibDecodeOptions(; kwargs...)
```

libzlibを使用したzlibデコンプレッション: https://www.zlib.net/

これはRFC 1950で説明されているzlibフォーマットです

# キーワード引数

  * `codec::ZlibCodec=ZlibCodec()`
