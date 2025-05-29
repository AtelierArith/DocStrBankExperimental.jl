`notebook(example::Type{<:Examples}; kwargs...)`

指定された `Examples` フォルダーのためにノートブックサーバーを起動します。

# 引数

  * `example::Type{<:Examples}`: 例のカテゴリ `JuliaExamples`、`PSYExamples`、`PSIExamples`、または `PSDExamples`
  * `notebook_target_dir = mktempdir()`: ノートブックを作成し、サーバーを起動するためのディレクトリ

# 例

`notebook(PSYExamples,  ".")`
