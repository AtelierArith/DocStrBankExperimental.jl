```
optimizer_model(model::InfiniteModel)::JuMP.Model
```

Return the JuMP model stored in `model` that is used to solve it.

**Example**

```julia-repl
julia> opt_model = optimizer_model(model)
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
