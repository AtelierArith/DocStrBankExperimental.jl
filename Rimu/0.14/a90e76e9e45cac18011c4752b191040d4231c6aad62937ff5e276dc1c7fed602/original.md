```
 FciqmcRunStrategy{T}
```

Abstract type representing the strategy for running and terminating [`lomc!()`](@ref). The type parameter `T` is relevant for reporting the shift and the norm.

Implemented strategies:

  * [`RunTillLastStep`](@ref)

!!! warning
    The use of this strategy is deprecated. Pass the relevant arguments directly to [`ProjectorMonteCarloProblem`](@ref) or to [`lomc!()`](@ref) instead.

