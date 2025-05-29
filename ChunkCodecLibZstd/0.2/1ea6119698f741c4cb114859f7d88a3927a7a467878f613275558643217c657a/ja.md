```
struct ZstdEncodeOptions <: EncodeOptions
ZstdEncodeOptions(; kwargs...)
```

Zstandard圧縮はlibzstdを使用しています: www.zstd.net

Zstandardのフォーマットは[RFC8878](https://datatracker.ietf.org/doc/html/rfc8878)に文書化されています。

# キーワード引数

  * `codec::ZstdCodec=ZstdCodec()`
  * `compressionLevel::Integer=0`: 圧縮レベル、通常のレベルは1-22です。

    レベル≥20は注意して使用する必要があります。なぜなら、より多くのメモリを必要とするからです。このライブラリは、速度と比率の好みの範囲を拡張する負の圧縮レベルも提供しています。レベルが低いほど、速度は速くなります（圧縮のコストがかかります）。0は`ZSTD_defaultCLevel()`の特別な値です。レベルは`ZSTD_minCLevel()`から`ZSTD_maxCLevel()`の範囲に制限されます。
  * `checksum::Bool=false`: フレームの最後にコンテンツの32ビットチェックサムが書き込まれます。
  * `advanced_parameters::Vector{Pair{Int32, Int32}}=[]`: `param => value`のペア。

    警告、一部のパラメータはデフォルトデコーダーと互換性のないエンコーディングを引き起こす可能性があります。一部のパラメータは実験的であり、新しいバージョンのlibzstdで変更される可能性があるため、[`ZSTD_versionNumber`](@ref)および[`ZSTD_cParam_getBounds`](@ref)を確認する必要があります。zstd.hのコメントを参照してください。追加のパラメータは`ZSTD_CCtx_setParameter`で設定されます。これらのパラメータは圧縮レベルとチェックサムオプションが設定された後に設定されるため、それらの値を上書きすることができます。ベクターはコンストラクタを呼び出した後に変更されてはなりません。
