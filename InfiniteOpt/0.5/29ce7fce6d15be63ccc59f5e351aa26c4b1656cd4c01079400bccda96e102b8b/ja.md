```
JuMP.set_optimizer(model::InfiniteModel,
                   [optimizer_constructor;
                   add_bridges::Bool = true])
```

`JuMP.set_optimizer`を拡張して無限モデルの最適化子を設定します。具体的には、最適化モデルの最適化子が変更されます。

**例**

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
