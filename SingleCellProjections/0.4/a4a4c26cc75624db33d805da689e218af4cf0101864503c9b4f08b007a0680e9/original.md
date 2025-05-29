```
ttest!(data::DataMatrix, h1, [group_a], [group_b]; h0, kwargs...)
```

Performs a t-Test with the given `h1` (alternative hypothesis) and `h0` (null hypothesis). Examples of t-Tests are Two-Group tests and Linear Regression.

`ttest!` adds a t-statistic, a p-value and a difference column to `data.var`.

See [`ttest_table`](@ref) for usage examples and more details on computations and parameters.

In addition `ttest!` supports the `kwarg`:

  * `prefix` - Output column names for t-statistics, p-values and differences will be prefixed with this string. If none is given, it will be constructed from `h1`, `group_a`, `group_b` and `h0`.

See also: [`ttest_table`](@ref), [`ttest`](@ref), [`ftest!`](@ref), [`mannwhitney!`](@ref)
