```
filter_matrix(fvar, fobs, data::DataMatrix)
```

Return a new DataMatrix, containing only the variables and observations passing the filters.

`fvar`/`fobs` can be:

  * An `AbstractVector` of indices to keep.
  * A `AbstractVector` of booleans (true to keep, false to discard).
  * `:` indicating that all variables/observations should be kept.
  * Anything you can pass on to `DataFrames.filter` (see [DataFrames documentation](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter) for details).

Also note that indexing of a DataMatrix supports `AbstractVector`s of indices/booleans and `:`, and is otherwise identical to `filter_matrix`.

# Examples

Keep every 10th variable and 3rd observation:

```julia
julia> filter_matrix(1:10:size(data,1), 1:3:size(data,2), data)
```

Or, using indexing syntax:

```julia
julia> data[1:10:end, 1:3:end]
```

For more examples, see `filter_var` and `filter_obs`.

See also: [`filter_var`](@ref), [`filter_obs`](@ref), [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)
