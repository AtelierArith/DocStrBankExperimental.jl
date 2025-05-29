tree2cartesian(t::AbstractVector) -> c::AbstractVector

Given quadtree coordinate, return the corresponding 2-D Cartesian coordinate.

# Examples

```jldoctest
julia> tree2cartesian([2,1,3])
2-element Array{Int64,1}:
 5
 2
```
