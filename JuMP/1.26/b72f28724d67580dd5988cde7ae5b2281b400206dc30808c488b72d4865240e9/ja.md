```
set_objective_coefficient(
    model::GenericModel{T},
    variable_1::GenericVariableRef{T},
    variable_2::GenericVariableRef{T},
    coefficient::Real,
) where {T}
```

`variable_1` と `variable_2` に関連付けられた二次目的係数を `coefficient` に設定します。

注意: この関数は非線形目的が設定されている場合にエラーをスローします。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @objective(model, Min, x[1]^2 + x[1] * x[2])
x[1]² + x[1]*x[2]

julia> set_objective_coefficient(model, x[1], x[1], 2)

julia> set_objective_coefficient(model, x[1], x[2], 3)

julia> objective_function(model)
2 x[1]² + 3 x[1]*x[2]
```
