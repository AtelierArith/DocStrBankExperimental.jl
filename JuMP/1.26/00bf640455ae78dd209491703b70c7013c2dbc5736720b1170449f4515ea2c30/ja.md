```
set_normalized_coefficient(
    constraints::AbstractVector{<:ConstraintRef},
    variables_1:AbstractVector{<:GenericVariableRef},
    variables_2:AbstractVector{<:GenericVariableRef},
    values::AbstractVector{<:Number},
)
```

`constraints`の`variables_1`と`variables_2`に関連する複数の二次係数を`values`に設定します。

このステップの前に、JuMPは同じ変数を含む複数の項を集約します。例えば、制約`2x^2 + 3x^2 <= 2`がある場合、`set_normalized_coefficient(con, [x], [x], [4])`は制約`4x^2 <= 2`を作成します。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @constraint(model, con, 2x[1]^2 + 3 * x[1] * x[2] + x[2] <= 2)
con : 2 x[1]² + 3 x[1]*x[2] + x[2] ≤ 2

julia> set_normalized_coefficient([con, con], [x[1], x[1]], [x[1], x[2]], [4, 5])

julia> con
con : 4 x[1]² + 5 x[1]*x[2] + x[2] ≤ 2
```
