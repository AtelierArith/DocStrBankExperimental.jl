```
DataFreeTree(treetype, data[, reorderbufffer = similar(data), kwargs...]) -> datafreetree
```

Creates a `DataFreeTree` which wraps a `KDTree` or `BallTree`. Keywords arguments are passed to their respective constructors.

The `KDTree` or `BallTree` will be stored without a reference to the underlaying data. `injectdata` has to be used to re-link them to a data array before use.
