```
λspacings(grid, ℓx, ℓy, ℓz)
```

Return a `KernelFunctionOperation` that computes the grid spacings for `grid` in the $λ$ direction at location `ℓx, ℓy, ℓz`.

# Examples

```jldoctest
julia> using Oceananigans

julia> grid = LatitudeLongitudeGrid(size=(36, 34, 25),
                                    longitude = (-180, 180),
                                    latitude = (-85, 85),
                                    z = (-1000, 0));

julia> λspacings(grid, Center(), Face(), Center())
KernelFunctionOperation at (Center, Face, Center)
├── grid: 36×34×25 LatitudeLongitudeGrid{Float64, Periodic, Bounded, Bounded} on CPU with 3×3×3 halo and with precomputed metrics
├── kernel_function: Δλ (generic function with 29 methods)
└── arguments: ("Center", "Face", "Center")
```
