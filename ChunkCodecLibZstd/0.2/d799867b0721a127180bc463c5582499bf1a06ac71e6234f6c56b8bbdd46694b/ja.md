```
struct ZstdDecodeOptions <: DecodeOptions
ZstdDecodeOptions(; kwargs...)
```

Zstandardのデcompressionはlibzstdを使用します: www.zstd.net

Zstandardのフォーマットは[RFC8878](https://datatracker.ietf.org/doc/html/rfc8878)に文書化されています。

# キーワード引数

  * `codec::ZstdCodec=ZstdCodec()`
  * `advanced_parameters::Vector{Pair{Int32, Int32}}=[]`: `param => value`のペア。

    警告、一部のパラメータは実験的であり、新しいバージョンのlibzstdで変更される可能性があるため、[`ZSTD_versionNumber`](@ref)および[`ZSTD_dParam_getBounds`](@ref)を確認する必要があるかもしれません。zstd.hのコメントを参照してください。追加のパラメータは`ZSTD_DCtx_setParameter`で設定されます。ベクターはコンストラクタを呼び出した後に変更されてはなりません。
