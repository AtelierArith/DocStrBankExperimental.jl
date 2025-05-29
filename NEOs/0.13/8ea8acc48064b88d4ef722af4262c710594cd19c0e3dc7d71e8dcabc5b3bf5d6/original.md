```
gaussiod(od::ODProblem{D, T}, params::NEOParameters{T}) where {D, T <: Real}
```

Fit a preliminary orbit to `od` via jet transport Gauss method.

See also [`gauss_method`](@ref).

## Arguments

  * `od::ODProblem{D, T}`: an orbit determination problem.
  * `params::NEOParameters{T}`: see `Gauss' Method Parameters` of [`NEOParameters`](@ref).
