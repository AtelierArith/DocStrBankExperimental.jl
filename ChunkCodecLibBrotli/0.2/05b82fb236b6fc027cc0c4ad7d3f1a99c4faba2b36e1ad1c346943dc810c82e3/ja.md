```
struct BrotliEncodeOptions <: EncodeOptions
BrotliEncodeOptions(; kwargs...)
```

brotli圧縮はbrotli Cライブラリを使用しています [https://brotli.org/](https://brotli.org/)

これはRFC 7932で説明されているbrotli (.br)フォーマットです

# キーワード引数

  * `codec::BrotliCodec=BrotliCodec()`
  * `quality::Integer=11`: 品質は0から11の間でなければなりません。

    0は最良の圧縮速度を提供し、11は最良の圧縮サイズを提供します。
  * `lgwin::Integer=24`: スライディングLZ77ウィンドウサイズは最大で`(1 << lgwin) - 16`です。

    10から24の間でなければなりません。エンコーダはこの値を減少させることがあります。例えば、入力がウィンドウサイズよりもはるかに小さい場合です。
  * `mode::Integer=0`: 特定の入力に合わせてエンコーダを調整します。

    0がデフォルトです。1はUTF-8テキスト用、2はWOFF 2.0用です。
