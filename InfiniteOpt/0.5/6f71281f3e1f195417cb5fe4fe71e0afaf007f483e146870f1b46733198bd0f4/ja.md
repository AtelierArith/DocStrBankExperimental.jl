```
JuMP.set_objective(model::InfiniteModel, sense::MOI.OptimizationSense,
                   func::Union{JuMP.AbstractJuMPScalar, Real})::Nothing
```

`JuMP.set_objective`を拡張して、無限モデル`model`の目的関数を設定します。`func`に無限の変数やパラメータが含まれている場合、またはモデルに属していない場合はエラーが発生します。

**例**

```julia-repl
julia> set_objective(model, MOI.MIN_SENSE, 2x + 1)

julia> objective_function(model)
2 x + 1
```
