```
minimum_xspacing(grid, ℓx, ℓy, ℓz)
```

Return the minimum spacing for `grid` in $x$ direction at location `ℓx, ℓy, ℓz`.

# Examples

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> minimum_xspacing(grid, Center(), Center(), Center())
0.5
```
