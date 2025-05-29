```
struct BloscEncodeOptions <: EncodeOptions
BloscEncodeOptions(; kwargs...)
```

Blosc圧縮はc-bloscライブラリを使用します: https://github.com/Blosc/c-blosc

# キーワード引数

  * `codec::BloscCodec=BloscCodec()`
  * `clevel::Integer=5`: 圧縮レベル、0（圧縮なし）から9（最大圧縮）までの範囲
  * `doshuffle::Integer=1`: シャッフルフィルターを使用するかどうか。

    0は適用しないことを意味し、1はバイトレベルで適用することを意味し、2はビットレベルで適用することを意味します（遅くなりますが、より良いエントロピー整列を達成できる可能性があります）。
  * `typesize::Integer=1`: シャッフル時に使用する要素サイズ。

    実装上の理由から、`1:255`の範囲内の`typesize`のみがシャッフルフィルターを機能させることができます。この範囲外の`typesize`の場合、シャッフルは静かに無効になります。
  * `compressor::AbstractString="lz4"`: 使用する圧縮機のタイプを表す文字列。

    例えば、"blosclz"、"lz4"、"lz4hc"、"zlib"、または"zstd"です。圧縮機がサポートされているかどうかを確認するには、`is_compressor_valid`を使用してください。
