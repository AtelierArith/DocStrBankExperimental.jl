```
hl_row(i::Number, crayon::Crayon) -> Highlighter
```

Highlight the entire row `i` with the `crayon`.

```
hl_row(rows::AbstractVector{Int}, crayon::Crayon) -> Highlighter
```

Highlights all the rows in `rows` with the `crayon`.

!!! info
    Those functions return a `Highlighter` to be used with the text backend.

