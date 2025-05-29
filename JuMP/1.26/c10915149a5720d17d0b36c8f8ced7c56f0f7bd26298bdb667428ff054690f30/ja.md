```
set_normalized_coefficient(
    constraint::ConstraintRef,
    variable::GenericVariableRef,
    value::Number,
)
```

制約 `constraint` における変数 `variable` の係数を `value` に設定します。

このステップの前に、JuMP は同じ変数を含む複数の項を集約します。例えば、制約 `2x + 3x <= 2` がある場合、`set_normalized_coefficient(con, x, 4)` は制約 `4x <= 2` を作成します。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, con, 2x + 3x <= 2)
con : 5 x ≤ 2

julia> set_normalized_coefficient(con, x, 4)

julia> con
con : 4 x ≤ 2
```
