cartesian2tree(c::AbstractVector) -> t::AbstractVector

Given a 2-D Cartesian coordinate, return the corresponding quadtree coordinate.

# Examples

```jldoctest
julia> cartesian2tree([5,2])
3-element Array{Int64,1}:
 2
 1
 3
```
