```
RTree{T,N}([K], V; kwargs...) where {T,N,V}
```

Construct `N`-dimensional [`RTree`](@ref) object that stores [`SpatialElem{T,N,K,V}`](@ref `SpatialElem`) elements. If `K` (the type of spatial element identifier) if not specified, the stored elements will not have ids.
