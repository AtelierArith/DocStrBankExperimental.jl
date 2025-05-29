```
getnormals(points::AbstractMatrix{T}; k::Integer=10)
```

## Description:

Compute the external normals of the points using the k-nearest method.

  * The input points should be a `N×3` array.
  * The output normals will be a `N×3` array.
