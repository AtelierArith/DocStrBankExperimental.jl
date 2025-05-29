```
isopenset(d::AbstractInterval)
```

Is the interval open set?

# Examples

```jldoctest
julia> isopenset(iv"[1,2]")
false

julia> isopenset(iv"(1,2]")
false

julia> isopenset(iv"[1,2)")
false

julia> isopenset(iv"(1,2)")
true
```
