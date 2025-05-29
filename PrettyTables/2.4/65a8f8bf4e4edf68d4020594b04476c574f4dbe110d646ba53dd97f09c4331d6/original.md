```
hl_row(i::Number, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

Highlight the entire row `i` with the `decoration`.

```
hl_row(rows::AbstractVector{Int}, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

Highlights all the rows in `rows` with the `decoration`.

!!! info
    Those functions return a `MarkdownHighlighter` to be used with the HTML backend.

