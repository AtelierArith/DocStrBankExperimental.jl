```
set_normalized_rhs(con_ref::ConstraintRef, value)
```

`constraint`の右辺項を`value`に設定します。

このステップの前に、JuMPはすべての定数項を制約の右辺に集約します。たとえば、制約`2x + 1 <= 2`がある場合、`set_normalized_rhs(con, 4)`は制約`2x <= 4`を作成します。`2x + 1 <= 4`にはなりません。

```jldoctest; setup = :(using JuMP; model = Model(); @variable(model, x)), filter=r"≤|<="
julia> @constraint(model, con, 2x + 1 <= 2)
con : 2 x <= 1.0

julia> set_normalized_rhs(con, 4)

julia> con
con : 2 x <= 4.0
```
