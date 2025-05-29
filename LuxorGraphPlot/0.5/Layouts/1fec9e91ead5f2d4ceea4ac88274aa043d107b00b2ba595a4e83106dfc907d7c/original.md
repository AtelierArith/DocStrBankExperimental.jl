```
SpringLayout <: AbstractLayout
```

A layout algorithm based on a spring model.

### Fields

  * `optimal_distance::Float64`: the optimal distance between vertices
  * `maxiter::Int`: the maximum number of iterations
  * `α0::Float64`: the initial moving speed
  * `meta::Dict{Symbol, Any}`: graph dependent meta information, including

      * `initial_locs`: initial vertex locations
      * `mask`: boolean mask for which vertices to relocate
