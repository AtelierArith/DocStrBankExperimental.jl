```
logtransform([T=Float64], counts::DataMatrix;
             var_filter = hasproperty(counts.var, "feature_type") ? "feature_type" => isequal("Gene Expression") : nothing,
             var_filter_cols = hasproperty(counts.var, "feature_type") ? "feature_type" : nothing,
             scale_factor=10_000,
             var=:copy,
             obs=:copy)
```

Log₂-transform `counts` using the formula:

```
  log₂(1 + cᵢⱼ*scale_factor/(∑ᵢcᵢⱼ))
```

Optionally, `T` can be specified to control the `eltype` of the sparse transformed matrix. `T=Float32` can be used to lower the memory usage, with little impact on the results, since downstream analysis is still done with Float64.

  * `var_filter` - Control which variables (features) to use for parameter estimation. Defaults to `"feature_type" => isequal("Gene Expression")`, if a `feature_type` column is present in `counts.var`. Can be set to `nothing` to disable filtering. See [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter) for how to specify filters.
  * `var_filter_cols` - Additional columns used to ensure features are unique. Defaults to "feature_type" if present in `counts.var`. Use a Tuple/Vector for specifying multiple columns. Can be set to `nothing` to not include any additional columns.
  * `var` - Can be `:copy` (make a copy of source `var`) or `:keep` (share the source `var` object).
  * `obs` - Can be `:copy` (make a copy of source `obs`) or `:keep` (share the source `obs` object).

# Examples

```julia
julia> transformed = logtransform(counts)
```

Use eltype Float32 to lower memory usage:

```julia
julia> transformed = logtransform(Float32, counts)
```

See also: [`sctransform`](@ref)
