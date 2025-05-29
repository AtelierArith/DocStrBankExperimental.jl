cartesian3tree(c::AbstractVector) -> t::AbstractVector

Given a 3-D Cartesian coordinate, return the corresponding octree coordinate.

# Examples

```jldoctest
julia> cartesian3tree([5,2,1])
3-element Array{Int64,1}:
 2
 1
 3
```
