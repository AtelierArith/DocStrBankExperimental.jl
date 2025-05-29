```
directedge(e::PeriodicEdge{D}) where D
directedge(src::PeriodicVertex{D}, dst::PeriodicVertex{D}) where D
directedge(src, dst, ofs::Union{SVector{D,T},NTuple{D,T}}) where {D,T}
```

Return the direct edge corresponding to `e = PeriodicEdge{D}(src, dst)`, i.e. `e` itself if `e` is direct, or `reverse(e)` otherwise.

## Examples

```jldoctest
julia> directedge(PeriodicEdge1D(3, 4, (0,)))
PeriodicEdge1D(3, 4, (0,))

julia> directedge(PeriodicEdge2D(5, 2, (0,0)))
PeriodicEdge2D(2, 5, (0,0))

julia> directedge(PeriodicEdge3D(3, 3, (0,-1,2)))
PeriodicEdge3D(3, 3, (0,1,-2))
```

See also [`isdirectedge`](@ref)
