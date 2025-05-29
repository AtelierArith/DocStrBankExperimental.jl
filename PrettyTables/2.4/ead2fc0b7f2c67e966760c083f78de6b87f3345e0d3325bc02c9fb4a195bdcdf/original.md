```
hl_col(i::Number, crayon::Crayon) -> Highlighter
```

Highlight the entire column `i` with the `crayon`.

```
hl_col(cols::AbstractVector{Int}, crayon::Crayon) -> Highlighter
```

Highlights all the columns in `cols` with the `crayon`.

!!! info
    Those functions return a `Highlighter` to be used with the text backend.

