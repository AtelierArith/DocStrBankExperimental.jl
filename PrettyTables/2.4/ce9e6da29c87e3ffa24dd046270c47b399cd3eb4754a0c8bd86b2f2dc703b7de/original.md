```
hl_row(i::Number, decoration::HtmlDecoration) -> HtmlHighlighter
```

Highlight the entire row `i` with the `decoration`.

```
hl_row(rows::AbstractVector{Int}, decoration::HtmlDecoration) -> HtmlHighlighter
```

Highlights all the rows in `rows` with the `decoration`.

!!! info
    Those functions return a `HtmlHighlighter` to be used with the HTML backend.

