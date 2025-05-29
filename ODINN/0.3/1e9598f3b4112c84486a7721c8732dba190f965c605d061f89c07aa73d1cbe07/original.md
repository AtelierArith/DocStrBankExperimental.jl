```
ContinuousAdjoint{
    F <: AbstractFloat,
    I <: Integer,
    VJP <: AbstractVJPMethod
    } <: AbstractAdjointMethod
```

Continuous adjoint of SIA2D with manual implementation of the backward in the ODE scheme.

# Fields

  * `VJP_method::VJP`: Type of AbstractVJPMethod used to compute VJPs inside adjoint   calculation.
  * `solver::Any`: The solver to be used for adjoint.
  * `reltol::F`: Relative tolerance to be used in the ODE solver of the adjoint.
  * `abstol::F`: Absolute tolerance to be used in the ODE solver of the adjoint.
  * `n_quadrature::I`: Number of nodes used in the Gauss quadrature for the numerical   integration of the loss function.
