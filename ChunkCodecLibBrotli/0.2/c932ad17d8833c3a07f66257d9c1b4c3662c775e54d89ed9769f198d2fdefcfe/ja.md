```
struct BrotliDecodeOptions <: DecodeOptions
BrotliDecodeOptions(; kwargs...)
```

brotli デコーディングは brotli C ライブラリを使用します [https://brotli.org/](https://brotli.org/)

これは RFC 7932 で説明されている brotli (.br) 形式です

# キーワード引数

  * `codec::BrotliCodec=BrotliCodec()`
