```
Query(text::AbstractString; replacements=AUTOMATIC_REPLACEMENTS) <: AbstractQuery
```

文字列の正確な一致を検索するためのクエリで、1つのフィールドがあります：

  * `text::String`

`text` は、`replacements` からの置換を適用することによって自動的に処理されます（デフォルトは [`AUTOMATIC_REPLACEMENTS`](@ref) です）。
