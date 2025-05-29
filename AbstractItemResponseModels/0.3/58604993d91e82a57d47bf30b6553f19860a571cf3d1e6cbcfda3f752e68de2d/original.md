```
iif(model::ItemResponseModel, theta, i)
iif(model::ItemResponseModel, theta, i, y)
```

## Arguments

  * `model`: An [`ItemResponseModel`](@ref)
  * `theta`: The person parameter value(s)
  * `i`: A unique item identifier
  * `y`: Response value(s)

## Return values

If `estimation_type(model) == PointEstimate` then the item information function must return a scalar value.

If `estimation_type(model) == SamplingEstimate` then the item information function must return a vector of values with the length equal to the number of samples drawn.
