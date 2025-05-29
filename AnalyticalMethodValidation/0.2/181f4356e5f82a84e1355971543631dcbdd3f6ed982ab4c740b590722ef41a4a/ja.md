```
pivot(df::DataFrame, col; rows = [], prefix = true, notsort = ["Stats", "File"], drop = [])
pivot(df::DataFrame, cols::AbstractVector; rows = [], prefix = true, notsort = ["Stats", "File"], drop = [])
```

`DataFrame`をワイドフォーマットに変換します。

# 引数

  * `df`: 対象の`DataFrame`。
  * `col`: ワイドフォーマットの列名を保持する列（シンボルまたは文字列）。
  * `cols`: ワイドフォーマットの列名を保持する列（ベクター）。

# キーワード引数

  * `rows`: ワイドフォーマットで行キーとして保持する列（シンボル、文字列、またはベクター）。
  * `prefix`: 列名に`col`または`cols`を保持するかどうか。
  * `notsort`: 列（ベクター）；これらの列でソートしない。
  * `drop`: 列（ベクター）；これらの列を削除する。
