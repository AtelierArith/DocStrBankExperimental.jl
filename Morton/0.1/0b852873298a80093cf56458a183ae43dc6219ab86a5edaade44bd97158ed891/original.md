```
morton3tree(m::Integer) -> t::AbstractVector
```

Given a Morton number, return the corresponding octree coordinate.

# Examples

```jldoctest
julia> morton3tree(67)
3-element Array{Any,1}:
 2
 1
 3
```
