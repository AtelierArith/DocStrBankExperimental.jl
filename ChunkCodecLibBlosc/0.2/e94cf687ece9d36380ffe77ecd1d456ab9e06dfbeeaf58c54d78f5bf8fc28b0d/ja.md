```
struct BloscDecodeOptions <: DecodeOptions
BloscDecodeOptions(; kwargs...)
```

c-bloscライブラリを使用したBloscのデコンプレッション: https://github.com/Blosc/c-blosc

# キーワード引数

  * `codec::BloscCodec=BloscCodec()`
