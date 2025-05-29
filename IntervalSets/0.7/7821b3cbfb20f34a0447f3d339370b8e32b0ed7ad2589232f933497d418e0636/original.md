```
closedendpoints(d::AI) where AI<:AbstractInterval
```

A tuple of `Bool`'s encoding whether the left/right endpoints are closed.

# Examples

```jldoctest
julia> closedendpoints(iv"[1,2]")
(true, true)

julia> closedendpoints(iv"(1,2]")
(false, true)

julia> closedendpoints(iv"[2,1)")
(true, false)

julia> closedendpoints(iv"(2,1)")
(false, false)
```
