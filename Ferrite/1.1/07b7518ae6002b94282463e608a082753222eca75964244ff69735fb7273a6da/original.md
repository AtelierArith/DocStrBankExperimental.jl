```
getneighborhood(topology, grid::AbstractGrid, cellidx::CellIndex, include_self=false)
getneighborhood(topology, grid::AbstractGrid, faceidx::FaceIndex, include_self=false)
getneighborhood(topology, grid::AbstractGrid, vertexidx::VertexIndex, include_self=false)
getneighborhood(topology, grid::AbstractGrid, edgeidx::EdgeIndex, include_self=false)
```

Returns all connected entities of the same type as defined by the respective topology. If `include_self` is true, the given entity is included in the returned list as well.
