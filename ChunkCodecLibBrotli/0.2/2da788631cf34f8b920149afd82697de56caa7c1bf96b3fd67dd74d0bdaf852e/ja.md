```
struct BrotliCodec <: Codec
BrotliCodec()
```

brotli 圧縮は brotli C ライブラリを使用しています [https://brotli.org/](https://brotli.org/)

これは RFC 7932 で説明されている brotli (.br) 形式です

[`BrotliEncodeOptions`](@ref) および [`BrotliDecodeOptions`](@ref) も参照してください
