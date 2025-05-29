```
AnalyteDataTable{A, S, N <: Real, T} <: AbstractDataTable{A, S, N, T}
```

タブularデータラッパーは、列の一部が分析物を表し、すべての行がサンプルを表すことを示します。 `A`は分析物のタイプを決定し、`S`はサンプルのタイプを決定し、`N`は数値の値のタイプを決定し、`T`はテーブルのタイプを決定します。

# フィールド

  * `analyte`: `Vector{A}`、ユーザー定義型の分析物、すなわち、`getproperty(table(dt), analytecol(dt))`。このフィールドを取得するには`analyteobj`を使用します。
  * `sample`: `Vector{S}`、ユーザー定義型のサンプル。このフィールドを取得するには`sampleobj`を使用します。
  * `analytecol`: `Symbol`、各要素が分析物名である列名。このフィールドを取得するには`analytecol`を使用します。
  * `table`: タイプ`T`のタブularデータ。このフィールドを取得するには`table`を使用します。

# プロパティ

`table`のすべてのプロパティ。
