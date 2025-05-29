```
mannwhitney(data::DataMatrix, column, [group_a, group_b]; var=:copy, obs=:copy, matrix=:keep, kwargs...)
```

Perform a Mann-Whitney U-test (also known as a Wilcoxon rank-sum test) between two groups of observations. The U statistic is corrected for ties, and p-values are computed using a normal approximation.

Note that `data` must be a `DataMatrix` containing a sparse matrix only. It is recommended to first [`logtransform`](@ref) (or [`tf_idf_transform`](@ref)) the raw counts before performing the Mann-Whitney U-test.

`mannwhitney` creates a copy of `data` and adds a U statistic and a p-value column to `data.var`. See [`mannwhitney!`](@ref) and [`mannwhitney_table`](@ref) for more details on groups and `kwargs`.

See also: [`mannwhitney!`](@ref), [`mannwhitney_table`](@ref)
