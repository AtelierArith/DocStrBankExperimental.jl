```
optimize(obj, p0::Vector{Float64}; lower_bounds=nothing, upper_bounds=nothing, vary=nothing)
```

Minimize the object function obj with initial parameters p0 using the IterativeNelderMeadOptimizer solver. Bounds can also be provided as additional `Vectors`. The `vary` keyword accepts an optional `BitVector` if certain parameters should remain fixed. Returns an NamedTuple with properties:

  * `pbest::Vector{Float64}`: The final parameters corresponding to the optimized objective value fbest.
  * `fbest::Float64`: The final optimized objective value.
  * `fcalls::Int`: The number of total objective calls.
  * `simplex::Matrix{Float64}`: The final simplex.
  * iteration::Int`: The number of iterations performed.
