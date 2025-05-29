```
zspacings(grid, ℓx, ℓy, ℓz)
```

Return a `KernelFunctionOperation` that computes the grid spacings for `grid` in the $z$ direction at location `ℓx, ℓy, ℓz`.

# Examples

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> zspacings(grid, Center(), Center(), Face())
KernelFunctionOperation at (Center, Center, Face)
├── grid: 2×4×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── kernel_function: Δz (generic function with 28 methods)
└── arguments: ("Center", "Center", "Face")
```
