```
density_pressure(u, equations)
```

Return the product of the [`density`](@ref) and the [`pressure`](@ref) associated to the conserved variables `u` for a given set of `equations`, e.g., the [`CompressibleEulerEquations2D`](@ref). This can be useful, e.g., as a variable for (shock-cappturing or AMR) indicators.

`u` is a vector of the conserved variables at a single node, i.e., a vector of the correct length `nvariables(equations)`.
