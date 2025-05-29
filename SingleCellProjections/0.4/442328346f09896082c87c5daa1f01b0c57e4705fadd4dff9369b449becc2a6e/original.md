```
SCTransformModel([T=Float64], counts::DataMatrix;
                 var_filter = hasproperty(counts.var, :feature_type) ? :feature_type => isequal("Gene Expression") : nothing,
                 rtol=1e-3, atol=0.0, annotate=true,
                 post_var_filter=:, post_obs_filter=:,
                 obs=:copy,
                 kwargs...)
```

Computes the `SCTransform` parameter estimates for `counts` and creates a SCTransformModel that can be applied to the same or another data set. Defaults to only using "Gene Expression" features.

Optionally, `T` can be specified to control the `eltype` of the sparse transformed matrix. `T=Float32` can be used to lower the memory usage, with little impact on the results, since downstream analysis is still done with Float64.

  * `var_filter` - Control which variables (features) to use for parameter estimation. Defaults to `"feature_type" => isequal("Gene Expression")`, if a `feature_type` column is present in `counts.var`. Can be set to `nothing` to disable filtering. See [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter) for how to specify filters.
  * `var_filter_cols` - Additional columns used to ensure features are unique. Defaults to "feature_type" if present in `counts.var`. Use a Tuple/Vector for specifying multiple columns. Can be set to `nothing` to not include any additional columns.
  * `rtol` - Relative tolerance when constructing low rank approximation.
  * `atol` - Absolute tolerance when constructing low rank approximation.
  * `annotate` - Set to true to include SCTransform parameter estimates as feature annotations.
  * `post_var_filter` - Equivalent to applying variable (feature) filtering after sctransform, but computationally more efficient.
  * `post_obs_filter` - Equivalent to applying observation (cell) filtering after sctransform, but computationally more efficient.
  * `obs` - Can be `:copy` (make a copy of source `obs`) or `:keep` (share the source `obs` object).
  * `kwargs...` - Additional `kwargs` are passed on to [`SCTransform.scparams`](https://github.com/rasmushenningsson/SCTransform.jl).

# Examples

Setup `SCTransformModel` (Gene Expression features):

```
julia> SCTransformModel(counts)
```

Setup `SCTransformModel` (Antibody Capture features):

```
julia> SCTransformModel(counts; var_filter = :feature_type => isequal("Antibody Capture"))
```

See also: [`sctransform`](@ref), [`SCTransform.scparams`](https://github.com/rasmushenningsson/SCTransform.jl), [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)
