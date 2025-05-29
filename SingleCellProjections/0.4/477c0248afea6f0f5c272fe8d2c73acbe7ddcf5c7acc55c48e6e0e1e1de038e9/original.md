```
normalize_matrix(data::DataMatrix, [covariates...]; center=true, scale=false, kwargs...)
```

Normalize `data`. By default, the matrix is centered. Any `covariates` specified (using column names of `data.obs`) will be regressed out.

  * `center` - Set to true to center the data matrix.
  * `scale` - Set to true to scale the variables in the data matrix to unit standard deviation.

For other `kwargs` and more detailed descriptions, see `NormalizationModel` and `designmatrix`.

# Examples

Centering only:

```julia
julia> normalize_matrix(data)
```

Regression model with intercept (centering) and "fraction_mt" (numerical annotation):

```julia
julia> normalize_matrix(data, "fraction_mt")
```

As above, but also including "batch" (categorical annotation):

```julia
julia> normalize_matrix(data, "fraction_mt", "batch")
```

See also: [`NormalizationModel`](@ref), [`designmatrix`](@ref)
