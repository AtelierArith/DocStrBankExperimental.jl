```
set_normalized_coefficient(con_ref::ConstraintRef, variable::VariableRef, value)
```

制約 `constraint` における `variable` の係数を `value` に設定します。

このステップの前に、JuMP は同じ変数を含む複数の項を集約します。例えば、制約 `2x + 3x <= 2` がある場合、`set_normalized_coefficient(con, x, 4)` は制約 `4x <= 2` を作成します。

```jldoctest; setup = :(using JuMP), filter=r"≤|<="
model = Model()
@variable(model, x)
@constraint(model, con, 2x + 3x <= 2)
set_normalized_coefficient(con, x, 4)
con

# output

con : 4 x <= 2.0
```
