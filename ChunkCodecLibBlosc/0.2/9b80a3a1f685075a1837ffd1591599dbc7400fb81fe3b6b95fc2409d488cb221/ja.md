```
struct BloscCodec <: Codec
BloscCodec()
```

c-bloscライブラリを使用したBlosc圧縮: https://github.com/Blosc/c-blosc

デコーディングは、圧縮ブロックに追加された余分なデータを受け付けません。デコーディングは、切り捨てられたデータや、複数の圧縮ブロックが連結されたものも受け付けません。

[`BloscEncodeOptions`](@ref)および[`BloscDecodeOptions`](@ref)を使用して、デコーディングおよびエンコーディングオプションを設定できます。
