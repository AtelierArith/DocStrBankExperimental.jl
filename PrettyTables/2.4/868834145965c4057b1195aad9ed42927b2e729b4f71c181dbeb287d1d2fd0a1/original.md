```
hl_col(i::Number, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

Highlight the entire column `i` with the `decoration`.

```
hl_col(cols::AbstractVector{Int}, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

Highlights all the columns in `cols` with the `decoration`.

!!! info
    Those functions return a `MarkdownHighlighter` to be used with the HTML backend.

