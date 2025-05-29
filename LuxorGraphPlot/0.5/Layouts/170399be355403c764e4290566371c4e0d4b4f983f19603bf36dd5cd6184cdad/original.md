```
StressLayout <: AbstractLayout
```

A layout algorithm based on stress majorization.

### Fields

  * `optimal_distance::Float64`: the optimal distance between vertices
  * `maxiter::Int`: the maximum number of iterations
  * `rtol::Float64`: the absolute tolerance
  * `initial_locs`: initial vertex locations
  * `mask`: boolean mask for which vertices to relocate
  * `meta::Dict{Symbol, Any}`: graph dependent meta information, including

      * `initial_locs`: initial vertex locations
      * `mask`: boolean mask for which vertices to relocate
