```
xspacings(grid, ℓx, ℓy, ℓz)
```

Return a `KernelFunctionOperation` that computes the grid spacings for `grid` in the $x$ direction at location `ℓx, ℓy, ℓz`.

# Examples

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> xspacings(grid, Center(), Center(), Center())
KernelFunctionOperation at (Center, Center, Center)
├── grid: 2×4×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── kernel_function: Δx (generic function with 29 methods)
└── arguments: ("Center", "Center", "Center")
```
