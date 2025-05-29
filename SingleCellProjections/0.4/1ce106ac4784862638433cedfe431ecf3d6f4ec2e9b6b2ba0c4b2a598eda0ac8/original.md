```
designmatrix(data::DataMatrix, [covariates...]; center=true, max_categories=100)
```

Creates a design matrix from `data.obs` and the given `covariates`. Covariates can be specied using strings (column name in data.obs), with autodetection of whether the covariate is numerical or categorical, or using the `covariate` function for more control.

  * `center` - If `true`, an intercept is added to the design matrix. (Should only be set to `false` in very rare circumstances.)
  * `max_categories` - Safety parameter, an error will be thrown if there are too many categories. In this case, it is likely a mistake that the covariate was used as a categorical covariate. Using a very large number of categories is also bad for performance and memory consumption.

# Examples

Centering only:

```julia
julia> designmatrix(data)
```

Regression model with intercept (centering) and "fraction_mt" (numerical annotation):

```julia
julia> designmatrix(data, "fraction_mt")
```

As above, but also including "batch" (categorical annotation):

```julia
julia> designmatrix(data, "fraction_mt", "batch")
```

See also: [`normalize_matrix`](@ref), [`NormalizationModel`](@ref), [`covariate`](@ref)
