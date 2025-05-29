```
quick_reg(
    data::FixedTable,
    f::FormulaTerm;
    minobs::Real=0.8,
    save_residuals::Bool=false
)

quick_reg(
    data::IterateFixedTable,
    f::FormulaTerm;
    minobs::Real=0.8,
    save_residuals::Bool=false
)
```

Calculates a linear regression for the supplied data based on the formula (formula from StatsModels.jl). Unless the formula explicitly excludes the intercept (i.e., `@formula(y ~ 0 + x)`), an intercept is added.

If `data` is of the type `IterateFixedTable`, then the function uses the maximum number of threads on each `FixedTable` in an optimized way and returns a `Vector{BasicReg}`.

## Arguments

  * `minobs::Real`: The minimum number of observations to return a completed regression. If less than 1,   the value is used as a percentage relative to the total number of business days in the time period.   Therefore, the default of 0.8 corresponds to at least 80% of the business days over the time period have values.
  * `save_residuals::Bool=false`: Whether to save the residuals into `BasicReg`, This can have significant performance implications.
