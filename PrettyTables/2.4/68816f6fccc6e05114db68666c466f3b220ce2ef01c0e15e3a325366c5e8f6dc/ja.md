```
hl_cell(i::Number, j::Number, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

セル `(i, j)` を `decoration` でハイライトします (詳細は [`MarkdownDecoration`](@ref) を参照)。

```
hl_cell(cells::AbstractVector{NTuple(2,Int)}, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

すべての `cells` を `decoration` でハイライトします (詳細は [`MarkdownDecoration`](@ref) を参照)。

!!! info
    これらの関数は、HTML バックエンドで使用するための `MarkdownHighlighter` を返します。

