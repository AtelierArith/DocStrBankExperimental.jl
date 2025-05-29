```
hl_cell(i::Number, j::Number, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

Highlight the cell `(i, j)` with the `decoration` (see [`MarkdownDecoration`](@ref)).

```
hl_cell(cells::AbstractVector{NTuple(2,Int)}, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

Highlights all the `cells` with the `decoration` (see [`MarkdownDecoration`](@ref)).

!!! info
    Those functions return a `MarkdownHighlighter` to be used with the HTML backend.

