```julia
struct ProjectedSystem
```

Object for a projected low level system. The projection is only valid for real Hamiltonians.

# Fields

  * `s`: Time grid (unitless) for projection
  * `ev`: Energy values for different levels
  * `dθ`: Geometric terms
  * `op`: Projected system bath interaction operators
  * `direct`: Direction for the calculation
  * `lvl`: Number of leves to keep
  * `ref`: Energy eigenstates at the final time
