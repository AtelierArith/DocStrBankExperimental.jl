```
minimum_yspacing(grid, ℓx, ℓy, ℓz)
```

Return the minimum spacing for `grid` in $y$ direction at location `ℓx, ℓy, ℓz`.

# Examples

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> minimum_yspacing(grid, Center(), Center(), Center())
0.25
```
