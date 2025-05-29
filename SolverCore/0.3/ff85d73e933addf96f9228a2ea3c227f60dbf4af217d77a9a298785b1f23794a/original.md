```
reset!(solver::AbstractOptimizationSolver, model::AbstractNLPModel)
```

Use in the context of restarting or reusing the `solver` structure. Reset the internal fields of `solver` for the `model` before calling `solve!` on the same structure. `model` must have the same number of variables, bounds and constraints as that used to instantiate `solver`.
