```
mannwhitney_table(data::DataMatrix, column, [group_a, group_b]; kwargs...)
```

Perform a Mann-Whitney U-test (also known as a Wilcoxon rank-sum test) between two groups of observations. The U statistic is corrected for ties, and p-values are computed using a normal approximation.

Note that `data` must be a `DataMatrix` containing a sparse matrix only. It is recommended to first [`logtransform`](@ref) (or [`tf_idf_transform`](@ref)) the raw counts before performing the Mann-Whitney U-test.

`column` specifies a column in `data.obs` and is used to determine which observations belong in which group.

If `group_a` and `group_b` are not given, the `column` must contain exactly two unique values (except `missing`). If `group_a` is given, but not `group_b`, the observations in group A are compared to all other observations (except `missing`). If both `group_a` and `group_b` are given, the observations in group A are compared the observations in group B.

`mannwhitney_table` returns a Dataframe with columns for variable IDs, U statistics and p-values.

Supported `kwargs` are:

  * `statistic_col="U"`   - Name of the output column containing the U statistics. (Set to nothing to remove from output.)
  * `pvalue_col="pValue"` - Name of the output column containing the p-values. (Set to nothing to remove from output.)
  * `h1_missing=:skip`    - One of `:skip` and `:error`. If `skip`, missing values in `column` are skipped, otherwise an error is thrown.

The following `kwargs` determine how the computations are threaded:

  * `nworkers`      - Number of worker threads used in the computation. Set to 1 to disable threading.
  * `chunk_size`    - Number of variables processed in each chunk.
  * `channel_size`  - Max number of unprocessed chunks in queue.

See also: [`mannwhitney!`](@ref), [`mannwhitney`](@ref)
