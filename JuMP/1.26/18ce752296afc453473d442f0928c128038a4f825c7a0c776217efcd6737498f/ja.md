```
objective_function_type(model::GenericModel)::AbstractJuMPScalar
```

目的関数の型を返します。

この関数は、[`MOI.ObjectiveFunctionType`](@ref) 属性を照会するのと同等です。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @objective(model, Min, 2 * x + 1);

julia> objective_function_type(model)
AffExpr (alias for GenericAffExpr{Float64, GenericVariableRef{Float64}})
```
