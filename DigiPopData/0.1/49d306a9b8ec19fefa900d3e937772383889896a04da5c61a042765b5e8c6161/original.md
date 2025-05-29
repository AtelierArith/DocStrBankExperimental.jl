```
mismatch_expression(sim::AbstractVector{<:Real}, metric::AbstractMetric, X::Vector{VariableRef}, X_len::Int) -> QuadExpr
```

## Arguments

  * `sim::AbstractVector{<:Real}`: A vector of simulated data.
  * `metric::AbstractMetric`: An instance of a metric descriptor (e.g., `MeanMetric`, `CategoryMetric`, etc.).
  * `X::Vector{VariableRef}`: A vector of JuMP variable references.
  * `X_len::Int`: The length of the vector of JuMP variable references.

Return an expression that quantifies the mismatch between simulated data `sim` and the target metric `metric`. The concrete formula depends on the subtype of `AbstractMetric`.
