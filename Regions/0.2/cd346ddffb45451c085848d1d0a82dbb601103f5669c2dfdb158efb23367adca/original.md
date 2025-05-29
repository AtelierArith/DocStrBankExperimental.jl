```
istouching(x::UnitRange{Int64}, y::UnitRange{Int64})
```

Test if two ranges touch.

```jldoctest
julia> using Regions

julia> istouching(0:10, 11:21)
true

julia> istouching(0:10, 12:22)
false
```
