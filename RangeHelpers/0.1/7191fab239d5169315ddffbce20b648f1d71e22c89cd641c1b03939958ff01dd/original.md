```
subdivide(r::AbstractRange, factor::Integer, mode=:walls)
```

Create a range with smaller step from `r`. Possible values for mode are (:walls, :centers).

```jldoctest
julia> using RangeHelpers

julia> r = 1:3.0
1.0:1.0:3.0

julia> subdivide(r, 2)
1.0:0.5:3.0

julia> subdivide(r, 4)
1.0:0.25:3.0

julia> subdivide(r, 2, mode=:walls)
1.0:0.5:3.0

julia> subdivide(r, 2, mode=:centers)
0.75:0.5:3.25

julia> subdivide(r, 10, mode=:centers)
0.55:0.1:3.45
```
