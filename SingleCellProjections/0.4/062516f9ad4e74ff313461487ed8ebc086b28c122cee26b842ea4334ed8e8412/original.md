```
ftest_table(data::DataMatrix, h1; h0, kwargs...)
```

Performs an F-Test with the given `h1` (alternative hypothesis) and `h0` (null hypothesis). Examples of F-Tests are ANOVA and Quadratic Regression, but any linear model can be used. (See "Examples" below for concrete examples.)

F-tests can be performed on any `DataMatrix`, but it is almost always recommended to do it directly after transforming the data using e.g. `sctransform`, `logtransform` or `tf_idf_transform`.

!!! note "Normalization"
    Do not use `ftest_table` after normalizing the data using `normalize_matrix`: `ftest_table` needs to know about the `h0` model (regressed out covariates) for correction computations. Failing to do so can result in incorrect results. If you want to correct for the same covariates, pass them as `h0` to `ftest_table`.


`h1` can be:

  * A string specifying a column name of `data.obs`. Auto-detection determines if the column is categorical (ANOVA) or numerical.
  * A [`covariate`](@ref) for more control of how to interpret the values in a column.
  * A tuple or vector of the above for compound models.

`ftest_table` returns a Dataframe with columns for variable IDs, F-statistics and p-values.

Supported `kwargs` are:

  * `h0`                  - Use a non-trivial `h0` (null) model. Specified in the same way as `h1` above.
  * `center=true`         - Add an intercept to the `h0` (null) model.
  * `statistic_col="F"`   - Name of the output column containing the F-statistics. (Set to nothing to remove from output.)
  * `pvalue_col="pValue"` - Name of the output column containing the p-values. (Set to nothing to remove from output.)
  * `h1_missing=:skip`    - One of `:skip` and `:error`. If `skip`, missing values in `h1` columns are skipped, otherwise an error is thrown.
  * `h0_missing=:error`   - One of `:skip` and `:error`. If `skip`, missing values in `h0` columns are skipped, otherwise an error is thrown.
  * `allow_normalized_matrix=false` - Set to true to accept running on a `DataMatrix` that has been normalized.

# Examples

Perform an ANOVA using the "celltype" annotation.

```julia
julia> ftest_table(transformed, "celltype")
```

Perform an ANOVA using the "celltype" annotation, while correcting for `fraction_mt` (a linear covariate).

```julia
julia> ftest_table(transformed, "celltype"; h0="fraction_mt")
```

Perform an ANOVA using the "celltype" annotation, while correcting for `fraction_mt` (a linear covariate) and "phase" (a categorical covariate).

```julia
julia> ftest_table(transformed, "celltype"; h0=("fraction_mt","phase"))
```

Perform Quadractic Regression using the covariate `x`, by first creating an annotation for `x` squared, and then using a compound model.

```julia
julia> data.obs.x2 = data.obs.x.^2;

julia> ftest_table(transformed, ("x","x2"))
```

See also: [`ftest!`](@ref), [`ftest`](@ref), [`ttest_table`](@ref), [`covariate`](@ref)
