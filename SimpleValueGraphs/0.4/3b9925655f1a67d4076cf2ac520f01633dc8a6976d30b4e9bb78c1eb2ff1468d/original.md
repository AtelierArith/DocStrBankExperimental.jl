```
ValMatrix{Tv, :< AbstractGraph, key}
```

A matrix view of the edge values for a specific key of a graph.

As this is as a view, the entries and the size of this matrix can change when the underlying graph changes. The view itself is immutable. Convert to a `Matrix` or `SparseMatrixCSC` to get a mutable matrix that does not change when the graph does.
