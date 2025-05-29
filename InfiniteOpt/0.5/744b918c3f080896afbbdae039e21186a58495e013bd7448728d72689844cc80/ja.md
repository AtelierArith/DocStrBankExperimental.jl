```
JuMP.objective_sense(model::InfiniteModel)::MOI.OptimizationSense
```

`JuMP.objective_sense` を拡張して、無限モデル `model` の目的の感覚を返します。

**例**

```julia-repl
julia> objective_sense(model)
MIN_SENSE::OptimizationSense = 0
```
