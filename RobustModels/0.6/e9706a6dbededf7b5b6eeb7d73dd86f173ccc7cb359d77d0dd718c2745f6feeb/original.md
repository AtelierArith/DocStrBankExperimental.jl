```
fit(::Type{M}, X::Union{AbstractMatrix{T},SparseMatrixCSC{T}},
    y::AbstractVector{T}; quantile::AbstractFloat=0.5,
    dofit::Bool          = true,
    wts::FPVector        = similar(y, 0),
    fitdispersion::Bool  = false,
    fitargs...) where {M<:QuantileRegression, T<:AbstractFloat}
```

Fit a quantile regression model with the model matrix (or formula) X and response vector (or dataframe) y.

It is solved using the exact interior method.

# Arguments

  * `X`: the model matrix (it can be dense or sparse) or a formula
  * `y`: the response vector or a dataframe.

# Keywords

  * `quantile::AbstractFloat=0.5`: the quantile value for the regression, between 0 and 1.
  * `dofit::Bool = true`: if `false`, return the model object without fitting;
  * `wts::Vector = []`: a weight vector, should be empty if no weights are used;
  * `fitdispersion::Bool = false`: reevaluate the dispersion;
  * `fitargs...`: other keyword arguments like `verbose` to print iteration details.

# Output

the RobustLinearModel object.
