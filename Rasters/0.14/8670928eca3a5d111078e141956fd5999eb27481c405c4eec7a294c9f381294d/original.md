```
points(A::AbstractRaster; dims=(YDim, XDim), ignore_missing) => Array{Tuple}
```

Returns a generator of the points in `A` for dimensions in `dims`, where points are a tuple of the values in each specified dimension index.

# Keywords

  * `dims` the dimensions to return points from. The first slice of other   layers will be used.
  * `ignore_missing`: wether to ignore missing values in the array when considering   points. If `true`, all points in the dimensions will be returned, if `false`   only the points that are not `=== missingval(A)` will be returned.

The order of `dims` determines the order of the points.

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
