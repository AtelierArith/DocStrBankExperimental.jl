```
GeneralizedQuantileEstimator{L<:LossFunction} <: AbstractQuantileEstimator
```

Generalized Quantile Estimator is an M-Estimator with asymmetric loss function.

For [`L1Loss`](@ref), this corresponds to quantile regression (although it is better to use [`quantreg`](@ref) for quantile regression because it gives the exact solution).

For [`L2Loss`](@ref), this corresponds to Expectile regression (see [`ExpectileEstimator`](@ref)).

# Fields

  * `loss`: the [`LossFunction`](@ref).
  * `τ`: the quantile value to estimate, between 0 and 1.

# Properties

  * `tau`, `q`, `quantile` are aliases for `τ`.
