```
isoverlapping(x::UnitRange{Int64}, y::UnitRange{Int64})
```

Test if two ranges overlap.

```jldoctest
julia> using Regions

julia> isoverlapping(0:10, 5:15)
true

julia> isoverlapping(0:10, 20:30)
false
```
