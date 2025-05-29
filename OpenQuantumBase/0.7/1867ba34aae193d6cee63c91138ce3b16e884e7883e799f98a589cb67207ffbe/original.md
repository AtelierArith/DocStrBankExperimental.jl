```julia
struct TimeDependentCouplings <: OpenQuantumBase.AbstractTimeDependentCouplings
```

Defines an 1-D array of time dependent system bath coupling operators.

# Fields

  * `coupling`: A tuple of single `TimeDependentCoupling` operators
