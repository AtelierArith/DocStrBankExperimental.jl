```
filter_var(f, data::DataMatrix; kwargs...)
```

Return a new DataMatrix, containing only the variables passing the filter.

`f` can be:

  * An `AbstractVector` of indices to keep.
  * A `AbstractVector` of booleans (true to keep, false to discard).
  * `:` indicating that all variables should be kept.
  * Anything you can pass on to `DataFrames.filter` (see [DataFrames documentation](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter) for details).

# Examples

Keep every 10th variable:

```julia
julia> filter_var(1:10:size(data,1), data)
```

Keep only variables of the type "Gene Expression":

```julia
julia> filter_var("feature_type"=>isequal("Gene Expression"), data)
```

See also: [`filter_matrix`](@ref), [`filter_obs`](@ref), [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)
