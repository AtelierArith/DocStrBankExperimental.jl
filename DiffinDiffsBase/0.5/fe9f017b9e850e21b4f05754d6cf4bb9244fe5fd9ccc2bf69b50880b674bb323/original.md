```
findcell(cols::VecColumnTable)
findcell(names, data, esample=Colon())
```

Group the row indices of a collection of data columns so that the combination of row values from these columns are the same within each group.

Instead of directly providing the relevant portions of columns as [`VecColumnTable`](@ref)``, one may specify the`names`of columns from`data`of any`Tables.jl`-compatible table type over selected rows indicated by`esample`. Note that unless`esample`covers all rows of`data`, the row indices are those for the subsample selected based on`esample`rather than those for the full`data`.

# Returns

  * `IdDict{Tuple, Vector{Int}}`: a map from unique row values to row indices.
