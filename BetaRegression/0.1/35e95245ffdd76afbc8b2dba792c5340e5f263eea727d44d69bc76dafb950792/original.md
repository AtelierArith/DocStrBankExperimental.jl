```
coeftable(model::BetaRegressionModel; level=0.95)
```

Return a table of the point estimates of the model parameters, their respective standard errors, $z$-statistics, Wald $p$-values, and confidence intervals at the given `level`. The precision parameter is included as the last row in the table.

The object returned by this function implements the [Tables.jl](https://github.com/JuliaData/Tables.jl/) interface for tabular data.
