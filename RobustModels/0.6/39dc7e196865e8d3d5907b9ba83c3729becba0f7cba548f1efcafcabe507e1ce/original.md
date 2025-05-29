```
fit!(m::RobustLinearModel; initial_scale::Union{Symbol, Real}=:mad,
          σ0::Union{Nothing, Symbol, Real}=initial_scale,
          initial_coef::AbstractVector=[],
          β0::AbstractVector=initial_coef,
          correct_leverage::Bool=false, kwargs...)
```

Optimize the objective of a `RobustLinearModel`.  When `verbose` is `true` the values of the objective and the parameters are printed on stdout at each iteration.

This function assumes that `m` was correctly initialized.

This function returns early if the model was already fitted, instead call `refit!`.
