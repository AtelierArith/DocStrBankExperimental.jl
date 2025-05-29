```
localmodel_tsp(s, γ::Int, τ, p::Int; method, ntype, stepsize)
localmodel_tsp(s, p::Int; method, ntype, stepsize)
```

Perform a timeseries prediction for `p` points, using local weighted modeling [1]. The function always returns an object of the same type as `s`, which can be either a timeseries (vector) or an `AbstractDataset` (trajectory), and the returned data always contains the final point of `s` as starting point. This means that the returned data has length of `p + 1`.

If given `(s, γ, τ)`, it first calls `reconstruct` (from `DelayEmbeddings`) on `s` with `(γ, τ)`. If given only `s` then no reconstruction is done.

## Keyword Arguments

  * `method = AverageLocalModel(ω_unsafe)` : Subtype of [`AbstractLocalModel`](@ref).
  * `ntype = FixedMassNeighborhood(2)` : Subtype of `AbstractNeighborhood` (from `DelayEmbeddings`).
  * `stepsize = 1` : Prediction step size.

## Description

Given a query point, the function finds its neighbors using neighborhood `ntype`. Then, the neighbors `xnn` and their images `ynn` are used to make a prediction for the future of the query point, using the provided `method`. The images `ynn` are the points `xnn` shifted by `stepsize` into the future.

The algorithm is applied iteratively until a prediction of length `p` has been created, starting with the query point to be the last point of the timeseries.

## References

[1] : D. Engster & U. Parlitz, *Handbook of Time Series Analysis* Ch. 1, VCH-Wiley (2006)
