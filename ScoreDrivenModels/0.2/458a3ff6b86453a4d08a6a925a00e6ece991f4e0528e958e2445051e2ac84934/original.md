```
IPNewton(model::ScoreDrivenModel, args...; kwargs...)
```

If an `Int` is provided the method will sample that many random initial_points and use them as initial points for Optim IPNewton method. If a `Vector{Vector{T}}` is provided it will use them as initial points for Optim IPNewton method.

This method provides an alternative to create box constraints. constraints can be passed as a Vector the default constraints are `ub = Inf * ones(T, dim_unknowns(model))` and `lb = -Inf * ones(T, dim_unknowns(model))`
