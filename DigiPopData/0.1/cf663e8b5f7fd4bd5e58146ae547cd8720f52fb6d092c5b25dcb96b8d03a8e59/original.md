```
mismatch(sim::AbstractVector{<:Real}, metric::AbstractMetric) -> Float64
```

## Arguments

  * `sim::AbstractVector{<:Real}`: A vector of simulated data.
  * `metric::AbstractMetric`: An instance of a metric descriptor (e.g., `MeanMetric`, `CategoryMetric`, etc.).

Return a loss that quantifies the mismatch between simulated data `sim` and the target metric `metric`.   The concrete formula depends on the subtype of `AbstractMetric`.
