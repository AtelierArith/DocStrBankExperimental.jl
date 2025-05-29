```
struct GzipDecodeOptions <: DecodeOptions
GzipDecodeOptions(; kwargs...)
```

libzlibを使用したgzipデコーディング: https://www.zlib.net/

これはRFC 1952で説明されているgzip (.gz)フォーマットです

# キーワード引数

  * `codec::GzipCodec=GzipCodec()`
