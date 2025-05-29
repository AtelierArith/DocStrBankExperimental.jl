```
AnalysisTable{A, S, T <: AbstractDataTable{A, S}}
```

異なるタイプの値を表す複数のテーブルのラッパー。`A`は分析物のタイプを決定し、`S`はサンプルのタイプを決定し、`T`はデータテーブルのタイプを決定します。これは`Dictionary{Symbol, T <: AbstractDataTable{A, S}}`として実装されていますが、辞書とは異なり、各データテーブルは`getproperty`を使用しても抽出できます。

# フィールド

  * `analyte`: `Vector{A}`、ユーザー定義タイプの分析物。`analyteobj`を使用してこのフィールドを取得します。
  * `sample`: `Vector{S}`、ユーザー定義タイプのサンプル。`sampleobj`を使用してこのフィールドを取得します。
  * `tables`: `Dictionary{Symbol, T}`、データタイプをデータテーブルにマッピングする辞書。`tables`を使用してこのフィールドを取得します。

# プロパティ

`tables`のすべてのキー。
