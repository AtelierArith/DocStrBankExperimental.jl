```
set_normalized_rhs(constraint::ConstraintRef, value::Number)
```

`constraint`の右辺項を`value`に設定します。

このステップの前に、JuMPはすべての定数項を制約の右辺に集約します。たとえば、制約`2x + 1 <= 2`がある場合、`set_normalized_rhs(con, 4)`は制約`2x <= 4`を作成し、`2x + 1 <= 4`にはなりません。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, con, 2x + 1 <= 2)
con : 2 x ≤ 1

julia> set_normalized_rhs(con, 4)

julia> con
con : 2 x ≤ 4
```
