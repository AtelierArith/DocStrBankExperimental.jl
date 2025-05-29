```
readstatallmeta(filepath; kwargs...)
```

ファイルパス `filepath` にあるサポートされているデータファイルから、フルデータを読み込まずに値ラベルを含むすべてのメタデータを返します。返される4つのオブジェクトは、ファイルレベルのメタデータ、変数名、変数レベルのメタデータ、および値ラベルそれぞれに対応しています。詳細は [`readstatmeta`](@ref) を参照してください。

# サポートされているファイル形式

  * Stata: `.dta`
  * SAS: `.sas7bdat` および `.xpt`
  * SPSS: `.sav` および `por`

# キーワード

  * `ext = lowercase(splitext(filepath)[2])`: パーサーを選択するためのデータファイルの拡張子。
  * `usecols::Union{ColumnSelector, Nothing} = nothing`: 指定された列（変数）からのみ変数レベルのメタデータを収集します。 `usecols=nothing` の場合はすべての列を収集します。
  * `file_encoding::Union{String, Nothing} = nothing`: ファイルの文字エンコーディングを手動で指定します。 `iconv` 互換の名前である必要があります。
  * `handler_encoding::Union{String, Nothing} = nothing`: ハンドラーの文字エンコーディングを手動で指定します。デフォルトは UTF-8 です。
