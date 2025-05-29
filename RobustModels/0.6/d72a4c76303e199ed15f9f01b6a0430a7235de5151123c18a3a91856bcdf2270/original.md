```
TauEstimator{L1<:BoundedLossFunction, L2<:BoundedLossFunction} <: AbstractMEstimator
```

τ-estimator for the given loss functions.

The τ-estimator corresponds to a M-estimation, where the loss function is a weighted sum of a high breakdown point loss and an efficient loss. The weight is recomputed at every step of the Iteratively Reweighted Least Square, so the estimate is both robust (high breakdown point) and efficient.

# Fields

  * `loss1`: the high breakdown point [`BoundedLossFunction`](@ref).
  * `loss2`: the high efficiency [`BoundedLossFunction`](@ref).
  * `w`: the weight in the sum of losses: `w . loss1 + loss2`.
