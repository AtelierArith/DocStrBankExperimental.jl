```
DiscreteAdjoint{VJP <: AbstractVJPMethod} <: AbstractAdjointMethod
```

Discrete adjoint of SIA2D with manual implementation of the backward in the ODE scheme.

# Fields

  * `VJP_method`: Type of AbstractVJPMethod used to compute VJPs inside adjoint   calculation.
