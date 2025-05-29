```
set_objective_coefficient(
    model::GenericModel,
    variable::GenericVariableRef,
    coefficient::Real,
)
```

`variable`に関連付けられた線形目的係数を`coefficient`に設定します。

注意: この関数は非線形目的が設定されている場合にエラーをスローします。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @objective(model, Min, 2x + 1)
2 x + 1

julia> set_objective_coefficient(model, x, 3)

julia> objective_function(model)
3 x + 1
```
