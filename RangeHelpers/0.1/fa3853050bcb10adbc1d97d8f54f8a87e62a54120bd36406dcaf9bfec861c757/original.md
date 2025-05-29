```
samegrid(r1::AbstractRange, r2::AbstractRange; atol=0, rtol=0, kw...)::Bool
```

Check if `r1` and `r2` are defined on the same grid. That is if there exist equal prolongations of `r1` and `r1`.

```jldoctest
julia> using RangeHelpers: samegrid

julia> samegrid(1:10, 11:12)
true

julia> samegrid(1:10, 11:1.1:12)
false

julia> samegrid(1:10, 1:0)
true

julia> samegrid(1:10, 0.1:0)
false

julia> samegrid(1:10, 5:-1:3)
true

julia> samegrid(1:10, 4.1:1:5, rtol=0.2)
true

```
