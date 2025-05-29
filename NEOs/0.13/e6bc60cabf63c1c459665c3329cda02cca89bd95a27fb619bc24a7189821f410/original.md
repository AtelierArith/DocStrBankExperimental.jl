```
orbitdetermination(od::ODProblem{D, T}, params::NEOParameters{T};
    kwargs...) where {D, I, T <: Real}
```

Initial Orbit Determination (IOD) routine.

## Arguments

  * `od::ODProblem{D, T}`: an orbit determination problem.
  * `params::NEOParameters{T}`: see [`NEOParameters`](@ref).

## Keyword arguments

  * `initcond::I`: naive initial conditions function; takes as input an   `AdmissibleRegion{T}` and outputs a `Vector{Tuple{T, T, Symbol}}`,   where each element has the form `(ρ, v_ρ, scale)`   (default: `iodinitcond`).

!!! warning
    This function will change the (global) `TaylorSeries` variables.

