```
information(model::ItemResponseModel, theta; scoring_function)
information(model::ItemResponseModel, theta, is; scoring_function)
```

Calculate the information of an [`ItemResponseModel`](@ref).

## Arguments

  * `theta`: The person parameter value(s)
  * `is`: One or multiple item identifiers. If `is` is omitted, the information of the whole test (test information) is returned.

## Keyword arguments

  * `scoring_function`: A binary function of the form `f(y, ctx) = x`, mapping all possible response values `y` to

a value `x`. The argument `ctx` contains the current item context.

## Return values

If `estimatione_type(model) == PointEstimate` then `information` must return a single scalar value.

If `estimation_type(model) == SamplingEstimate` then `information` must return a vector of values with the length equal to the number of samples drawn.
