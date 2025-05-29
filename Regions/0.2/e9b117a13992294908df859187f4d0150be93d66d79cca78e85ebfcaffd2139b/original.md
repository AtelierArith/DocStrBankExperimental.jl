```
invert(x::UnitRange{Int64})
```

Inverts a range. Inversion mirrors a range at the origin. A range is  inverted by reversing and inverting each of its coordinates.

```jldoctest
julia> using Regions

julia> invert(5:10)
-10:-5

julia> invert(invert(0:100))
0:100
```
