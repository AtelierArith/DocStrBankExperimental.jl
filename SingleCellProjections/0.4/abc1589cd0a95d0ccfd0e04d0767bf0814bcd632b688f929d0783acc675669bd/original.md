```
filter_obs(f, data::DataMatrix)
```

Return a new DataMatrix, containing only the observations passing the filter.

`f` can be:

  * An `AbstractVector` of indices to keep.
  * A `AbstractVector` of booleans (true to keep, false to discard).
  * `:` indicating that all observations should be kept.
  * Anything you can pass on to `DataFrames.filter` (see DataFrames documentation for details).

# Examples

Keep every 10th observation:

```julia
julia> filter_obs(1:10:size(data,2), data)
```

Remove observations where "celltype" equals "other":

```julia
julia> filter_obs("celltype"=>!isequal("other"), data)
```

See also: [`filter_matrix`](@ref), [`filter_var`](@ref), [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)
