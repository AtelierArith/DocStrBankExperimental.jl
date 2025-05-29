```
Document(text::AbstractString, metadata::T; replacements=AUTOMATIC_REPLACEMENTS) where {T<:NamedTuple}
```

単一の文字列ドキュメントを表します。このオブジェクトには2つのフィールドがあります。

  * `text::String`
  * `metadata::T`

`text`は、デフォルトで[`AUTOMATIC_REPLACEMENTS`](@ref)からの置換を適用し、ドキュメントの先頭と末尾にスペースを追加することによって自動的に処理されます（すでに存在しない場合）。
