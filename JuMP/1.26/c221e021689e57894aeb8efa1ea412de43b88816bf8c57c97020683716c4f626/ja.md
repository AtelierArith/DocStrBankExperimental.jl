```
objective_function(
    model::GenericModel,
    ::Type{F} = objective_function_type(model),
) where {F}
```

目的関数を表す型 `F` のオブジェクトを返します。

目的が型 `F` に変換できない場合はエラーになります。

この関数は、[`MOI.ObjectiveFunction{F}`](@ref) 属性を照会するのと同等です。

## 例

```jldoctest objective_function
julia> model = Model();

julia> @variable(model, x)
x

julia> @objective(model, Min, 2x + 1)
2 x + 1

julia> objective_function(model, AffExpr)
2 x + 1

julia> objective_function(model, QuadExpr)
2 x + 1

julia> typeof(objective_function(model, QuadExpr))
QuadExpr (alias for GenericQuadExpr{Float64, GenericVariableRef{Float64}})
```

最後の2つのコマンドから、目的関数がアフィンであっても、二次関数に変換可能であれば、二次関数として照会でき、その結果が二次的であることがわかります。

しかし、変数には変換できません：

```jldoctest objective_function; filter = r"MathOptInterface\."s
julia> objective_function(model, VariableRef)
ERROR: InexactError: convert(MathOptInterface.VariableIndex, 1.0 + 2.0 MOI.VariableIndex(1))
[...]
```
