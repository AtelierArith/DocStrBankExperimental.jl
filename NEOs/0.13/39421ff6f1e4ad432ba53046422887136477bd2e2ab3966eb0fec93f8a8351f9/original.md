```
tsaiod(od::ODProblem{D, T}, params::NEOParameters{T};
    initcond::I = iodinitcond) where {D, I, T <: Real}
```

Fit a preliminary orbit to `od` via jet transport minimization of the normalized mean square residual over the manifold of variations.

## Arguments

  * `od::ODProblem{D, T}`: an orbit determination problem.
  * `params::NEOParameters{T}`: see `Too Short Arc Parameters` of [`NEOParameters`](@ref).

## Keyword arguments

  * `initcond::I`: naive initial conditions function; takes as input an   `AdmissibleRegion{T}` and outputs a `Vector{Tuple{T, T, Symbol}}`,   where each element has the form `(ρ, v_ρ, scale)`   (default: `iodinitcond`).
