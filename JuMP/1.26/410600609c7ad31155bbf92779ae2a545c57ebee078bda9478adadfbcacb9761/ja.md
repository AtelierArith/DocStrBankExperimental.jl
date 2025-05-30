```
set_objective_coefficient(
    model::GenericModel,
    variables::Vector{<:GenericVariableRef},
    coefficients::Vector{<:Real},
)
```

`variables` に関連付けられた複数の線形目的係数を `coefficients` に設定します。1 回の呼び出しで行います。

注意: この関数は、非線形目的が設定されている場合にエラーをスローします。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> @objective(model, Min, 3x + 2y + 1)
3 x + 2 y + 1

julia> set_objective_coefficient(model, [x, y], [5, 4])

julia> objective_function(model)
5 x + 4 y + 1
```
