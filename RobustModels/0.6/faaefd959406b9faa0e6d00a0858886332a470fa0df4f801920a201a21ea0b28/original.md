```
fit!(m::QuantileRegression;
     verbose::Bool=false,
     quantile::Union{Nothing, AbstractFloat}=nothing,
     correct_leverage::Bool=false,
     kwargs...)
```

Optimize the objective of a `QuantileRegression`.  When `verbose` is `true` the values of the objective and the parameters are printed on stdout at each function evaluation.

This function assumes that `m` was correctly initialized. This function returns early if the model was already fitted, instead call `refit!`.
