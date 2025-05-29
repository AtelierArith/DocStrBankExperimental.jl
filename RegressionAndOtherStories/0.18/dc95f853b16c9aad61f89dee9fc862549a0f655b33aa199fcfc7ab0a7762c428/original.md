Compute median, mad_sd, mean and std summary of distribution.

```julia
model_summary(df, params; round_estimates, digits)

```

## Positional arguments

```julia
* `df::DataFrame` # DataFrame holding the draws
* `params` # Vector of Symbols or Strings to be included
```

## Keyword arguments

```julia
* `round_estimates=true` # Round to `digits` decimals.
* `digits = 3` # Number of decimal digits
* `table_header_type=eltype(params)` # Symbol or String
```
