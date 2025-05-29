```
uncertaintyparameter(od::ODProblem{D, T}, sol::NEOSolution{T, T},
    params::NEOParameters{T}) where {D, T <: Real}
```

Return the Minor Planet Center Uncertainty Parameter.

## Arguments

  * `od::ODProblem{D, T}`: an orbit determination problem.
  * `sol::NEOSolution{T, T}:` reference orbit.
  * `params::NEOParameters{T}`: see [`NEOParameters`](@ref).

!!! reference
    https://www.minorplanetcenter.net/iau/info/UValue.html


!!! warning
    This function will change the (global) `TaylorSeries` variables.

