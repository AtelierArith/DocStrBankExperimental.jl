```
set_objective(model::AbstractModel, sense::MOI.OptimizationSense, func)
```

[`@objective`](@ref) マクロの機能的同等物です。

目的の感覚と目的関数を同時に設定し、次のように等価です：

```julia
set_objective_sense(model, sense)
set_objective_function(model, func)
```

## 例

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
set_objective(model, MIN_SENSE, x)
```
