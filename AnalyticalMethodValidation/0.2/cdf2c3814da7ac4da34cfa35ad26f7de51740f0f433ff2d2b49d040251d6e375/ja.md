```
unpivot(df::DataFrame, col; rows = [], notsort = ["Stats", "File"], drop = [])
unpivot(df::DataFrame, cols::AbstractVector; rows = [], notsort = ["Stats", "File"], drop = [])
```

`DataFrame`をワイドフォーマットに変換します。

# 引数

  * `df`: 対象の`DataFrame`。
  * `col`: ロングフォーマットの列名（シンボルまたは文字列）。
  * `cols`: ロングフォーマットの列（ベクター）。

# キーワード引数

  * `rows`: ロングフォーマットで行キーとして保持する列（シンボル、文字列、またはベクター）。
  * `notsort`: 列（ベクター）；これらの列でソートしない。
  * `drop`: 列（ベクター）；これらの列を削除する。
