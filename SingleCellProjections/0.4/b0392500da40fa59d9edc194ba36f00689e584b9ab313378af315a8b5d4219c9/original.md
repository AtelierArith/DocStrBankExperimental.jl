```
ftest!(data::DataMatrix, h1; h0, kwargs...)
```

Performs an F-Test with the given `h1` (alternative hypothesis) and `h0` (null hypothesis). Examples of F-Tests are ANOVA and Quadratic Regression, but any linear model can be used.

`ftest!` adds a F-statistic and a p-value column to `data.var`.

See [`ftest_table`](@ref) for usage examples and more details on computations and parameters.

In addition `ftest!` supports the `kwarg`:

  * `prefix` - Output column names for F-statistics and p-values will be prefixed with this string. If none is given, it will be constructed from `h1` and `h0`.

See also: [`ftest_table`](@ref), [`ftest`](@ref), [`ttest!`](@ref)
