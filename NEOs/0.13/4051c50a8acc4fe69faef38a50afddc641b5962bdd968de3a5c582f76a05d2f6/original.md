```
orbitdetermination(od::ODProblem{D, T}, sol::NEOSolution{T, T},
    params::NEOParameters{T}) where {D, T <: Real}
```

Fit a least squares orbit to `od` using `sol` as an initial condition.

## Arguments

  * `od::ODProblem{D, T}`: orbit determination problem.
  * `sol::NEOSolution{T, T}:` preliminary orbit.
  * `params::NEOParameters{T}`: see [`NEOParameters`](@ref).

!!! warning
    This function will change the (global) `TaylorSeries` variables.

