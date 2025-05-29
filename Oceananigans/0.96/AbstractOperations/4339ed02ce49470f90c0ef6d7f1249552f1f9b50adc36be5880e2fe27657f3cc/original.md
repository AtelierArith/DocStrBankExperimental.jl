```
yspacings(grid, ℓx, ℓy, ℓz)
```

Return a `KernelFunctionOperation` that computes the grid spacings for `grid` in the $y$ direction at location `ℓx, ℓy, ℓz`.

# Examples

```jldoctest
julia> using Oceananigans

julia> grid = RectilinearGrid(size=(2, 4, 8), extent=(1, 1, 1));

julia> yspacings(grid, Center(), Face(), Center())
KernelFunctionOperation at (Center, Face, Center)
├── grid: 2×4×8 RectilinearGrid{Float64, Periodic, Periodic, Bounded} on CPU with 2×3×3 halo
├── kernel_function: Δy (generic function with 29 methods)
└── arguments: ("Center", "Face", "Center")
```
