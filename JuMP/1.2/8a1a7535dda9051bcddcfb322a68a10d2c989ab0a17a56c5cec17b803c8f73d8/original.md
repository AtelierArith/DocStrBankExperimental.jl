```
Model()
```

Return a new JuMP model without any optimizer; the model is stored in a cache.

Use [`set_optimizer`](@ref) to set the optimizer before calling [`optimize!`](@ref).
