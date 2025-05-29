tree3cartesian(t::AbstractVector) -> c::AbstractVector

Given octree coordinate, return the corresponding 3-D Cartesian coordinate.

# Examples

```jldoctest
julia> tree3cartesian([2,1,3])
3-element Array{Int64,1}:
 5
 2
 1
```
