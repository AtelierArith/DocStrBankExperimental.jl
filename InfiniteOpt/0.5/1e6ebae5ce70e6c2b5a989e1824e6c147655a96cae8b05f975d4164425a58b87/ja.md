```
JuMP.set_objective_sense(model::InfiniteModel,
                         sense::MOI.OptimizationSense)::Nothing
```

`JuMP.set_objective_sense`を拡張して、無限モデル`model`の目的の感覚を設定します。

**例**

```julia-repl
julia> set_objective_sense(model, MOI.MIN_SENSE)

julia> objective_sense(model)
MIN_SENSE::OptimizationSense = 0
```
