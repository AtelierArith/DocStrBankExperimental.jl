```
hl_cell(i::Number, j::Number, crayon::Crayon) -> Highlighter
```

Highlight the cell `(i,j)` with the `crayon`.

```
hl_cell(cells::AbstractVector{NTuple(2,Int)}, crayon::Crayon) -> Highlighter
```

Highlights all the `cells` with the `crayon`.

!!! info
    Those functions return a `Highlighter` to be used with the text backend.

