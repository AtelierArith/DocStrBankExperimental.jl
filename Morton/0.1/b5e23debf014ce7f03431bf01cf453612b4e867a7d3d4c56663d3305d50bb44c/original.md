```
morton2tree(m::Integer) -> t::AbstractVector
```

Given a Morton number, return the corresponding quadtree coordinate.

# Examples

```jldoctest
julia> morton2tree(19)
3-element Array{Any,1}:
 2
 1
 3
```
