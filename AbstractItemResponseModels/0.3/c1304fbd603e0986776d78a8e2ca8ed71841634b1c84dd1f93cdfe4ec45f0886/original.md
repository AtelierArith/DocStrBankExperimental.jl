```
expected_score(model::ItemResponseModel, theta; scoring_function)
expected_score(model::ItemResponseModel, theta, is; scoring_function)
```

Calculate the expected score of an [`ItemResponseModel`](@ref).

## Arguments

  * `model`: An [`ItemResponseModel`](@ref)
  * `theta`: The person parameter value(s)
  * `is`: One or multiple item identifiers. If `is` is omitted, the expected score for the whole test is returned.

## Keyword arguments

  * `scoring_function`: A binary function of the form `f(y, ctx) = x`, mapping all possible response values `y` to

a value `x`. The argument `ctx` contains the current item context.

## Return values

If `estimation_type(model) == PointEstimate` then `expected_score` must return a single scalar value.

If `estimation_type(model) == SamplingEstimate` then `expected_score` must return a vector of values with the length equal to the number of samples drawn.
