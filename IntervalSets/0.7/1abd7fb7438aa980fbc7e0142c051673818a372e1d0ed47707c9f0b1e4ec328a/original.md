```
isclosedset(d::AbstractInterval)
```

Is the interval closed set?

# Examples

```jldoctest
julia> isclosedset(iv"[1,2]")
true

julia> isclosedset(iv"(1,2]")
false

julia> isclosedset(iv"[1,2)")
false

julia> isclosedset(iv"(1,2)")
false
```
