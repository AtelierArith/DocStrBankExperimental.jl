```
isleftopen(d::AbstractInterval)
```

Is the interval open at the left endpoint?

# Examples

```jldoctest
julia> isleftopen(iv"[1,2]")
false

julia> isleftopen(iv"(2,1)")
true
```
