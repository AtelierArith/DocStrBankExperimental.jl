```
CellField(data, grid)
```

Return a `CellField` with its `data` located on the `grid`. if `data` is the same *total* size of a `CellField`, `data` is wrapped in an `OffsetArray`. Otherwise, `data` must be settable to a `CellField` of `size(grid)`.
