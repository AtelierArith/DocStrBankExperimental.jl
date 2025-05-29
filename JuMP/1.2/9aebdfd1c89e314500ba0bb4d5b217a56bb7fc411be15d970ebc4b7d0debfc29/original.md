```
struct NoOptimizer <: Exception end
```

No optimizer is set. The optimizer can be provided to the [`Model`](@ref) constructor or by calling [`set_optimizer`](@ref).
