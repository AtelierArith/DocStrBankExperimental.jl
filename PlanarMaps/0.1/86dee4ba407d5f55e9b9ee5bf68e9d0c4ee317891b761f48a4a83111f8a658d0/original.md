```
add_edge!(P::PlanarMap,i::Integer,j::Integer,F::Face)
add_edge!(P::PlanarMap,i::Integer,j::Integer)
```

Add edge from `i` to `j` through the face `F` in the planar map `P`. If `F` is not given, the face discovered first in the `NeighborCycle` of `i` will be used
