```
localmodel_cp(source_pool, target_pool, source_pred,  γ, τ; kwargs...)
```

Perform a cross prediction from  *source* to *target*, using local weighted modeling [1]. `source_pred` is the input for the prediction and `source_pool` and `target_pool` are used as pooling/training data for the predictions. The function always returns an object of the same type as `target_pool`, which can be either a timeseries (vector) or an `AbstractDataset` (trajectory).

## Keyword Arguments

  * `method = AverageLocalModel(ω_unsafe)` : Subtype of [`AbstractLocalModel`](@ref).
  * `ntype = FixedMassNeighborhood(2)` : Subtype of `AbstractNeighborhood` (from `DelayEmbeddings`).
  * `stepsize = 1` : Prediction step size.

Instead of passing `γ` & `τ` for reconstruction one may also give existing `Dataset`s as `source_pool` and `source_pred`. In this case an additional keyword argument `y_idx_shift::Int=0` may be necessary to account for the index shift introduced in the reconstruction process.

## Description

Given a query point, the function finds its neighbors using neighborhood `ntype`. Then, the neighbors `xnn` and their images `ynn` are used to make a prediction for the image of the query point, using the provided `method`.

## References

[1] : D. Engster & U. Parlitz, *Handbook of Time Series Analysis* Ch. 1, VCH-Wiley (2006)
