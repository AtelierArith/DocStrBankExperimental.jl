```
ftest(data::DataMatrix, h1; h0, var=:copy, obs=:copy, matrix=:keep, kwargs...)
```

Performs an F-Test with the given `h1` (alternative hypothesis) and `h0` (null hypothesis). Examples of F-Tests are ANOVA and Quadratic Regression, but any linear model can be used.

`ftest` creates a copy of `data` and adds a F-statistic and a p-value column to `data.var`.

See [`ftest_table`](@ref) and [`ftest!`](@ref) for usage examples and more details on computations and parameters.

See also: [`ftest!`](@ref), [`ftest_table`](@ref), [`ttest`](@ref)
