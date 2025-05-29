```
hl_cell(i::Number, j::Number, decoration::HtmlDecoration) -> HtmlHighlighter
```

セル `(i, j)` を `decoration` でハイライトします (詳細は [`HtmlDecoration`](@ref) を参照)。

```
hl_cell(cells::AbstractVector{NTuple(2,Int)}, decoration::HtmlDecoration) -> HtmlHighlighter
```

すべての `cells` を `decoration` でハイライトします (詳細は [`HtmlDecoration`](@ref) を参照)。

!!! info
    これらの関数は HTML バックエンドで使用するための `HtmlHighlighter` を返します。

