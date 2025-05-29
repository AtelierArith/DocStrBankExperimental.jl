```
struct Bins{Dim, M, CRS}
```

A container type for bins of dimension `Dim` embedded in manifold `M` with coordinate reference system `CRS`.

### Fields

  * `bins`: A vector of `Polytope{Dim, M, CRS}` objects.

### Methods

```
points(bins)
```

Return a vector of raw vertices for each bin.
