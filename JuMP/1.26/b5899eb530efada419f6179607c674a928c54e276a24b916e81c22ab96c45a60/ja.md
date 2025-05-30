```
set_objective_coefficient(
    model::GenericModel{T},
    variables_1::AbstractVector{<:GenericVariableRef{T}},
    variables_2::AbstractVector{<:GenericVariableRef{T}},
    coefficients::AbstractVector{<:Real},
) where {T}
```

`variables_1` と `variables_2` に関連付けられた複数の二次目的係数を `coefficients` に設定します。一度の呼び出しで行います。

注意: この関数は非線形目的が設定されている場合にエラーをスローします。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @objective(model, Min, x[1]^2 + x[1] * x[2])
x[1]² + x[1]*x[2]

julia> set_objective_coefficient(model, [x[1], x[1]], [x[1], x[2]], [2, 3])

julia> objective_function(model)
2 x[1]² + 3 x[1]*x[2]
```
