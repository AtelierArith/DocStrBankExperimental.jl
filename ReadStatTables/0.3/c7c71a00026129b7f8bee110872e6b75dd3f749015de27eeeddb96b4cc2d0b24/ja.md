```
readstat(filepath; kwargs...)
```

`filepath`にあるサポートされているデータファイルからデータ（メタデータを含む）を収集する[`ReadStatTable`](@ref)を返します。

# サポートされているファイル形式

  * Stata: `.dta`
  * SAS: `.sas7bdat`および`.xpt`
  * SPSS: `.sav`および`por`

# キーワード

  * `ext = lowercase(splitext(filepath)[2])`: パーサーを選択するためのデータファイルの拡張子。
  * `usecols::Union{ColumnSelector, Nothing} = nothing`: 指定された列（変数）からのみデータを収集します。`usecols=nothing`の場合はすべての列を収集します。
  * `row_limit::Union{Integer, Nothing} = nothing`: 読み取る行の総数を制限します。`row_limit=nothing`の場合はすべての行を読み取ります。
  * `row_offset::Integer = 0`: 指定された行数をスキップします。
  * `ntasks::Union{Integer, Nothing} = nothing`: 複数のスレッドで同時にデータファイルを読み取るために生成されるタスクの数。`ntasks`が`nothing`または1未満の場合、データファイルのサイズと利用可能なスレッドの数（`Threads.nthreads()`）に基づいてデフォルト値を選択します。メタデータから行数が不明な`.xpt`および`.por`ファイルには適用されません。
  * `apply_value_labels::Bool = true`: 関連する列に値ラベルを適用します。
  * `inlinestring_width::Integer = ext ∈ (".sav", ".por") ? 0 : 32`: `inlinestring_width`および`pool_width`未満の幅を持つ任意の文字列変数に対してインラインで保存できる固定幅文字列型を使用します。非正の値はインライン文字列型の使用を避けます。SPSSファイルには推奨されません。
  * `pool_width::Integer = 64`: 幅が少なくとも64の文字列変数に対してのみ`PooledArray`の使用を試みます。
  * `pool_thres::Integer = 500`: ユニークな値の数が`pool_thres`を超える場合、文字列変数に対して`PooledArray`を使用しません。非正の値は`PooledArray`の使用を避けます。
  * `file_encoding::Union{String, Nothing} = nothing`: ファイルの文字エンコーディングを手動で指定します。`iconv`互換の名前である必要があります。
  * `handler_encoding::Union{String, Nothing} = nothing`: ハンドラーの文字エンコーディングを手動で指定します。デフォルトはUTF-8です。
