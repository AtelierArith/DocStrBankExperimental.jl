```
 distance(p1, p2; method = CentroidToCentroid())
```

Find the distance between `Parcel`s `p1` and `p2` using `method` (one of  `CentroidToCentroid()` or `ClosestVertices`). This method call will expect to find a distance matrix `:distances` belonging to the first parcel's `SurfaceSpace` struct
