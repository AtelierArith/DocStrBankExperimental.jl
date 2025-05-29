```
MMEstimator{L1<:BoundedLossFunction, L2<:LossFunction} <: AbstractMEstimator
```

MM-estimator for the given loss functions.

The MM-estimator is obtained using a two-step process:

1. compute a robust scale estimate with a high breakdown point using a S-estimate and the loss function `L1`.
2. compute an efficient estimate using a M-estimate with the loss function `L2`.

# Fields

  * `loss1`: the [`BoundedLossFunction`](@ref) used for the high breakdown point S-estimation.
  * `loss2`: the [`LossFunction`](@ref) used for the efficient M-estimation.
  * `scaleest`: boolean specifying the if the estimation is in the S-estimation step (`true`)

or the M-estimation step (`false`).
