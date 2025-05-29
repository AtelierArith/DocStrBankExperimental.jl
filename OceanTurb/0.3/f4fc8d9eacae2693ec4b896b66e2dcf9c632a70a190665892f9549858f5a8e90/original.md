```
FaceField(data, grid)
```

Return a `FaceField` with its `data` located on the `grid`. if `data` is the same *total* size of a `FaceField`, `data` is wrapped in an `OffsetArray`. Otherwise, `data` must be settable to a `FaceField` of `size(grid)`.
