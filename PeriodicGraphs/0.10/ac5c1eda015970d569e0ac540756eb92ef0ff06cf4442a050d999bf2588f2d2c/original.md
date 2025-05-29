```
isdirectedge(e::PeriodicEdge)
```

Return `true` if `e` is direct, in the sense being of the form `(u, v, ofs)` with either `u < v` or `u == v && ofs > zero(ofs)`.

An edge `e` is indirect iff `reverse(e)` is not.

## Examples

```jldoctest
julia> isdirectedge(PeriodicEdge1D(3, 4, (0,)))
true

julia> isdirectedge(PeriodicEdge2D(5, 2, (0,0)))
false

julia> isdirectedge(PeriodicEdge3D(3, 3, (0,-1,2)))
false
```

See also [`directedge`](@ref)
