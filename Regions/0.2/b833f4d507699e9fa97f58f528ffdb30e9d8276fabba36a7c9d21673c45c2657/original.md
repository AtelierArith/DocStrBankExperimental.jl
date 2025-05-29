```
invert(x::Run)
```

Invert a run. Inversions mirrors a run at the origin. A run is inverted by negating  its row and inverting its columns.

In addition to the invert method, you can also use the unary - operator.

```jldoctest reg
julia> using Regions

julia> invert(Run(1, 20:30))
Run(-1, -30:-20)

julia> -Run(-1, -30:-20)
Run(1, 20:30)
```
