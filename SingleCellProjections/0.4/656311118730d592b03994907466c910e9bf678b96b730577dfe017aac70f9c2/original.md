```
ttest(data::DataMatrix, h1, [group_a], [group_b]; h0, var=:copy, obs=:copy, matrix=:keep, kwargs...)
```

Performs a t-Test with the given `h1` (alternative hypothesis) and `h0` (null hypothesis). Examples of t-Tests are Two-Group tests and Linear Regression.

`ttest` creates a copy of `data` and adds a t-statistic, a p-value and a difference column to `data.var`.

See [`ttest_table`](@ref) and [`ttest!`](@ref) for usage examples and more details on computations and parameters.

See also: [`ttest!`](@ref), [`ttest_table`](@ref), [`ftest`](@ref), [`mannwhitney`](@ref)
