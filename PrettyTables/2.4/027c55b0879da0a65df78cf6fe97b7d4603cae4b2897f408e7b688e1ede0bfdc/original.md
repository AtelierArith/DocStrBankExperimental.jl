```
hl_col(i::Number, decoration::HtmlDecoration) -> HtmlHighlighter
```

Highlight the entire column `i` with the `decoration`.

```
hl_col(cols::AbstractVector{Int}, decoration::HtmlDecoration) -> HtmlHighlighter
```

Highlights all the columns in `cols` with the `decoration`.

!!! info
    Those functions return a `HtmlHighlighter` to be used with the HTML backend.

