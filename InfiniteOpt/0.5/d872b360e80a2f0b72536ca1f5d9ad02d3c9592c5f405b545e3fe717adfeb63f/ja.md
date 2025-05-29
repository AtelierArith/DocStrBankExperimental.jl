```
JuMP.set_objective_function(model::InfiniteModel, func::Real)::Nothing
```

`JuMP.set_objective_function`を拡張して、数値で`model`の目的式を設定します。

**例**

```jldoctest; setup = :(using InfiniteOpt, JuMP; model = InfiniteModel())
julia> set_objective_function(model, 3)

julia> objective_function(model)
3
```
