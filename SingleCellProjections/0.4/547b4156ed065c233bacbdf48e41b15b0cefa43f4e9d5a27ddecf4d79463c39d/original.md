```
ttest_table(data::DataMatrix, h1, [group_a], [group_b]; h0, kwargs...)
```

Performs a t-Test with the given `h1` (alternative hypothesis) and `h0` (null hypothesis). Examples of t-Tests are Two-Group tests and Linear Regression.

T-tests can be performed on any `DataMatrix`, but it is almost always recommended to do it directly after transforming the data using e.g. `sctransform`, `logtransform` or `tf_idf_transform`.

!!! note "Normalization"
    Do not use `ttest_table` after normalizing the data using `normalize_matrix`: `ttest_table` needs to know about the `h0` model (regressed out covariates) for correction computations. Failing to do so can result in incorrect results. If you want to correct for the same covariates, pass them as `h0` to `ttest_table`.


`h1` can be:

  * A string specifying a column name of `data.obs`. Auto-detection determines if the column is categorical (Two-Group) or numerical (linear regression).

      * If `group_a` and `group_b` are specified, a Two-Group test between `group_a` and `group_b` is performed.
      * If `group_a` is specified, but not `group_b`, a Two-Group test between `group_a` and all other observations is performed.
  * A [`covariate`](@ref) for more control of how to interpret the values in the column.

`ttest_table` returns a Dataframe with columns for variable IDs, t-statistics, p-values and differences. For Two-group tests, `difference` is the difference in mean between the two groups. For linear regression, the difference corresponds to the rate of change.

Supported `kwargs` are:

  * `h0`                            - Use a non-trivial `h0` (null) model. Specified in the same way as `h1` above.
  * `center=true`                   - Add an intercept to the `h0` (null) model.
  * `statistic_col="t"`             - Name of the output column containing the t-statistics. (Set to nothing to remove from output.)
  * `pvalue_col="pValue"`           - Name of the output column containing the p-values. (Set to nothing to remove from output.)
  * `difference_col="difference"`   - Name of the output column containing the differences. (Set to nothing to remove from output.)
  * `h1_missing=:skip`              - One of `:skip` and `:error`. If `skip`, missing values in `h1` columns are skipped, otherwise an error is thrown.
  * `h0_missing=:error`             - One of `:skip` and `:error`. If `skip`, missing values in `h0` columns are skipped, otherwise an error is thrown.
  * `allow_normalized_matrix=false` - Set to true to accept running on a `DataMatrix` that has been normalized.

# Examples

Perform a Two-Group t-test between celltypes "Mono" and "DC".

```julia
julia> ttest_table(transformed, "celltype", "Mono", "DC")
```

Perform a Two-Group t-test between celltype "Mono" and all other cells.

```julia
julia> ttest_table(transformed, "celltype", "Mono")
```

Perform a Two-Group t-test between celltypes "Mono" and "DC", while correcting for "fraction_mt" (a linear covariate).

```julia
julia> ttest_table(transformed, "celltype", "Mono", "DC")
```

Perform Linear Regression using the covariate "fraction_mt".

```julia
julia> ttest_table(transformed, "fraction_mt")
```

See also: [`ttest!`](@ref), [`ttest`](@ref), [`ftest_table`](@ref), [`mannwhitney_table`](@ref), [`covariate`](@ref)
