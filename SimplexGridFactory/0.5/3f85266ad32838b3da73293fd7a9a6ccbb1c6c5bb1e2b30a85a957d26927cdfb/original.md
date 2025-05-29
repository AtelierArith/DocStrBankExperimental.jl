```julia
mutable struct BinnedPointList{T}
```

Binned point list structure allowing for fast  check for already existing points.

This provides better performance for indendifying  already inserted points than the naive linear search.

OTOH the implementation is still quite naive - it dynamically maintains a cuboid bining region with a fixed number of bins. 

Probably tree based adaptive methods (a la octree) will be more efficient, however they will be harder to implement.

In an ideal world, we would maintain a dynamic Delaunay triangulation, which at once could be the starting point of mesh generation which will follow here anyway.
