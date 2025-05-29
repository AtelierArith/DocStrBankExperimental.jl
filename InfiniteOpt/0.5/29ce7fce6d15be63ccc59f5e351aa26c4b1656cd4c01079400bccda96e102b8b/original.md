```
JuMP.set_optimizer(model::InfiniteModel,
                   [optimizer_constructor;
                   add_bridges::Bool = true])
```

Extend `JuMP.set_optimizer` to set optimizer of infinite models. Specifically, the optimizer of the optimizer model is modified.

**Example**

```julia-repl
julia> set_optimizer(model, Clp.Optimizer)

julia> optimizer_model(model)
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: EMPTY_OPTIMIZER
Solver name: SolverName() attribute not implemented by the optimizer.
```
