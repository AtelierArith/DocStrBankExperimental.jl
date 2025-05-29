```
irf(model::ItemResponseModel, theta, i)
irf(model::ItemResponseModel, theta, i, y)
```

Evaluate the item response function of an [`ItemResponseModel`](@ref).

## Arguments

  * `model`: An [`ItemResponseModel`](@ref)
  * `theta`: The person parameter value(s)
  * `i`: A unique item identifier
  * `y`: Response value(s)

## Return values

If `estimation_type(model) == PointEstimate` then the item response function must return a scalar value.

If `estimation_type(model) == SamplingEstimate` then the item response function must return a vector of values with the length equal to the number of samples.
