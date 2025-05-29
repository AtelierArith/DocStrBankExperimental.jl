```
hl_cell(i::Number, j::Number, decoration::HtmlDecoration) -> HtmlHighlighter
```

Highlight the cell `(i, j)` with the `decoration` (see [`HtmlDecoration`](@ref)).

```
hl_cell(cells::AbstractVector{NTuple(2,Int)}, decoration::HtmlDecoration) -> HtmlHighlighter
```

Highlights all the `cells` with the `decoration` (see [`HtmlDecoration`](@ref)).

!!! info
    Those functions return a `HtmlHighlighter` to be used with the HTML backend.

