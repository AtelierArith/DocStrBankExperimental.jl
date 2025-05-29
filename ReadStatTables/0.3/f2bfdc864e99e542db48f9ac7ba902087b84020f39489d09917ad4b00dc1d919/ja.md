```
readstatmeta(filepath; kwargs...)
```

ファイルレベルのメタデータを収集する[`ReadStatMeta`](@ref)を返しますが、`filepath`にあるサポートされたデータファイルから完全なデータを読み込むことはありません。 [`readstatallmeta`](@ref)も参照してください。

# サポートされているファイル形式

  * Stata: `.dta`
  * SAS: `.sas7bdat`および`.xpt`
  * SPSS: `.sav`および`por`

# キーワード

  * `ext = lowercase(splitext(filepath)[2])`: パーサーを選択するためのデータファイルの拡張子。
  * `file_encoding::Union{String, Nothing} = nothing`: ファイルの文字エンコーディングを手動で指定します。`iconv`互換の名前である必要があります。
  * `handler_encoding::Union{String, Nothing} = nothing`: ハンドラーの文字エンコーディングを手動で指定します。デフォルトはUTF-8です。
