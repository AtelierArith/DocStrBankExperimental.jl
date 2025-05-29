```
coeftable(model::StatisticalModel; level::Real=0.95)
```

Return a table with coefficients and related statistics of the model. `level` determines the level for confidence intervals (by default, 95%).

The returned `CoefTable` object implements the [Tables.jl](https://github.com/JuliaData/Tables.jl/) interface, and can be converted e.g. to a `DataFrame` via `using DataFrames; DataFrame(coeftable(model))`.
