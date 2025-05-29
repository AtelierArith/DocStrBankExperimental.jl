```
objective_sense(model::GenericModel)::MOI.OptimizationSense
```

目的の感覚を返します。

この関数は、[`MOI.ObjectiveSense`](@ref) 属性を照会するのと同等です。

## 例

```jldoctest
julia> model = Model();

julia> objective_sense(model)
FEASIBILITY_SENSE::OptimizationSense = 2

julia> @variable(model, x);

julia> @objective(model, Max, x)
x

julia> objective_sense(model)
MAX_SENSE::OptimizationSense = 1
```
