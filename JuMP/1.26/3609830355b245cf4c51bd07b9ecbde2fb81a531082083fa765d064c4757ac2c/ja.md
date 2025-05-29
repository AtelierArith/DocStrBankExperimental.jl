```
set_normalized_coefficient(
    constraint::ConstraintRef,
    variable_1:GenericVariableRef,
    variable_2:GenericVariableRef,
    value::Number,
)
```

`constraint`内の`variable_1`と`variable_2`に関連付けられた二次係数を`value`に設定します。

このステップの前に、JuMPは同じ変数を含む複数の項を集約します。例えば、制約`2x^2 + 3x^2 <= 2`がある場合、`set_normalized_coefficient(con, x, x, 4)`は制約`4x^2 <= 2`を作成します。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @constraint(model, con, 2x[1]^2 + 3 * x[1] * x[2] + x[2] <= 2)
con : 2 x[1]² + 3 x[1]*x[2] + x[2] ≤ 2

julia> set_normalized_coefficient(con, x[1], x[1], 4)

julia> set_normalized_coefficient(con, x[1], x[2], 5)

julia> con
con : 4 x[1]² + 5 x[1]*x[2] + x[2] ≤ 2
```
