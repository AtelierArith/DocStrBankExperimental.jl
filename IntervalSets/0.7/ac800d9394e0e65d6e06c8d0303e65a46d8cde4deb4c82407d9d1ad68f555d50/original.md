```
isleftclosed(d::AbstractInterval)
```

Is the interval closed at the left endpoint?

# Examples

```jldoctest
julia> isleftclosed(iv"[1,2]")
true

julia> isleftclosed(iv"(2,1)")
false
```
