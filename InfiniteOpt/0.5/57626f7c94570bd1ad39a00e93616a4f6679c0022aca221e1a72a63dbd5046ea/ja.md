```
JuMP.set_objective_function(model::InfiniteModel,
                            func::JuMP.AbstractJuMPScalar)::Nothing
```

`JuMP.set_objective_function`を拡張して、無限モデル`model`の目的式を設定します。`func`に無限の変数やパラメータが含まれている場合はエラーになります。また、`func`に無効な変数が含まれている場合もエラーになります。

**例**

```julia-repl
julia> set_objective_function(model, 2x + 1)

julia> objective_function(model)
2 x + 1
```
