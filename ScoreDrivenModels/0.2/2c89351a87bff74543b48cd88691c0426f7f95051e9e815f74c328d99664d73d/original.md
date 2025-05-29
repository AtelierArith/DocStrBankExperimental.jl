```
LBFGS(model::ScoreDrivenModel, args...; kwargs...)
```

If an `Int` is provided the method will sample that many random initial_points and use them as initial points for Optim LBFGS method. If a `Vector{Vector{T}}` is provided it will use them as initial points for Optim LBFGS method.
