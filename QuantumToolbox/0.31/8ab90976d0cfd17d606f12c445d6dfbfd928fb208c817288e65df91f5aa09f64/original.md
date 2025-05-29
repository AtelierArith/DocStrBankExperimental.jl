```
tracedist(ρ::QuantumObject, σ::QuantumObject)
```

Calculates the [trace distance](https://en.wikipedia.org/wiki/Trace_distance) between two [`QuantumObject`](@ref): $T(\hat{\rho}, \hat{\sigma}) = \frac{1}{2} \lVert \hat{\rho} - \hat{\sigma} \rVert_1$

Note that `ρ` and `σ` must be either [`Ket`](@ref) or [`Operator`](@ref).
