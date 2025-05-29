```
DataFrames.DataFrame(
    covar::CovarianceMatrix,
    othercols::Dict = Dict{Symbol,Any}();
    delete_duplicate_correlations::Bool = true,
)
```

Convert a CovarianceMatrix to a `DataFrame` format.

### Inputs

  * `covar` - The `CovarianceMatrix`
  * `othercols` - This adds columns to the `DataFrame`. For instance if it is `Dict{Symbol,String}([:pc] .=> ["Fred's PC"])`, then there will be a column indicating that this estimation was done on Fred's PC.
  * `delete_duplicate_correlations` - Should the unnecessary correlations be included (as correlation matrices are symmetric half the entries duplicate information).

### Returns

  * A `DataFrame`.
