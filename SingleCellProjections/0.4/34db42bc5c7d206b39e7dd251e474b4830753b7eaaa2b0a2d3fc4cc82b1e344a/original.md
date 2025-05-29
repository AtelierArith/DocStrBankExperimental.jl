```
mannwhitney!(data::DataMatrix, column, [group_a, group_b]; kwargs...)
```

Perform a Mann-Whitney U-test (also known as a Wilcoxon rank-sum test) between two groups of observations. The U statistic is corrected for ties, and p-values are computed using a normal approximation.

Note that `data` must be a `DataMatrix` containing a sparse matrix only. It is recommended to first [`logtransform`](@ref) (or [`tf_idf_transform`](@ref)) the raw counts before performing the Mann-Whitney U-test.

`mannwhitney!` adds a U statistic and a p-value column to `data.var`. See [`mannwhitney_table`](@ref) for more details on groups and kwargs.

In addition `mannwhitney!` supports the `kwarg`:

  * `prefix` - Output column names for U statistics and p-values will be prefixed with this string. If none is given, it will be constructed from `column`, `group_a` and `group_b`.

See also: [`mannwhitney_table`](@ref), [`mannwhitney`](@ref)
