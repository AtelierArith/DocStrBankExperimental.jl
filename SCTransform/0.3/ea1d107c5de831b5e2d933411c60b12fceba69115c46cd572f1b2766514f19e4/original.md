```
sctransform(X::AbstractSparseMatrix, features, params;
            transpose = false,
            feature_id_columns = [:id,:feature_type],
            feature_type,
            feature_mask,
            cell_ind = 1:size(X,2),
            clip=sqrt(size(X,2)/30))
```

Computes the SCTransform of the sparse matrix `X`, with features as rows and cells as columns. `features` should be a table (e.g. DataFrame or NamedTuple) with feature annotations. `params` is a table with reguralized feature parameter estimates - typically estimated using the function `scparams`.

  * `transpose` - set to true to transpose the output (cells as rows, features as columns).
  * `feature_id_columns` is a vector of column names in `features`. The rows in `features` must be unique based on these columns.
  * `feature_type` - Convenience parameter used for `feature_mask` default. Defaults to "Gene Expression" if `features` has a `feature_type` column.
  * `feature_mask` - Vector of booleans deciding which features to use. If set explicitly, the `feature_type` parameter is ignored, otherwise `feature_mask` defaults to only choosing the `feature_type` specified. Affects how logcellcounts are computed. Normally expected to match `feature_mask` used when calling `scparams`.
  * `cell_ind` is vector of cell indices to include in the output. This is computationally more efficient than subsetting afterwards, but yields the same result.
  * `clip` - values less than `-clip` or larger than `clip` are clamped, to reduce the impact of outliers.

See also: [`scparams`](@ref)
