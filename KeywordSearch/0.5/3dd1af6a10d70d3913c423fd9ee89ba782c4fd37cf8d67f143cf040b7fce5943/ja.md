```
FuzzyQuery(text, dist, threshold; replacements=AUTOMATIC_REPLACEMENTS) <: AbstractQuery
```

文字列のあいまいな一致を検索するためのクエリで、3つのフィールドがあります：

  * `text::String`: 一致させるテキスト
  * `dist::D`: 使用する距離測定; デフォルトは `DamerauLevenshtein()`
  * `threshold::T`: 一致に許可される最大しきい値; デフォルトは2。

`text`は、`replacements`（デフォルトは [`AUTOMATIC_REPLACEMENTS`](@ref)）を適用することによって自動的に処理されます。
