```
selectby(df::DataFrame, col, col_pairs...; 
        pivot = false, 
        rows = [], 
        notsort = ["Stats", "File"], 
        prefix = true, 
        drop = [], 
        kwargs...)
```

`col`によって値を選択し、値が列であるかのように`select!`を適用します。

# 引数

  * `df`: 対象の`DataFrame`。
  * `col`: 列名。
  * `col_pairs`: 列を操作するための`DataFrames.jl`構文。内部の`select!`関数に渡されます。

# キーワード引数

  * `rows`: 行キーとして保持する列（シンボル、文字列、またはベクター）。
  * `pivot`: `col`によってデータフレームをピボットするかどうか。
  * `notsort`: 列（ベクター）；これらの列でソートしない。
  * `drop`: 列（ベクター）；これらの列を削除する。
  * `kwargs`: 内部の`select!`関数のためのキーワード引数。
