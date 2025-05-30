```
set_objective_sense(model::GenericModel, sense::MOI.OptimizationSense)
```

モデルの目的の感覚を指定された感覚に設定します。

関連情報: [`@objective`](@ref), [`set_objective_function`](@ref), [`set_objective`](@ref)

## FEASIBILITY_SENSE

目的の感覚を [`FEASIBILITY_SENSE`](@ref) に設定すると、既存の目的が削除されます。

## 例

```jldoctest
julia> model = Model();

julia> objective_sense(model)
FEASIBILITY_SENSE::OptimizationSense = 2

julia> set_objective_sense(model, MOI.MAX_SENSE)

julia> objective_sense(model)
MAX_SENSE::OptimizationSense = 1
```
