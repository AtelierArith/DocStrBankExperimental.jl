```
minimum_zspacing(grid, ℓx, ℓy, ℓz)
minimum_zspacing(grid) = minimum_zspacing(grid, Center(), Center(), Center())
```

Return the minimum spacing for `grid` in $z$ direction at location `ℓx, ℓy, ℓz`.

# Examples

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> minimum_zspacing(grid, Center(), Center(), Center())
0.125
```
