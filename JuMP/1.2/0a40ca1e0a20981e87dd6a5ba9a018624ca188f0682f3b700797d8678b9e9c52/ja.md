```
add_to_function_constant(constraint::ConstraintRef, value)
```

`value`を関数の定数項に追加します。

スカラー制約の場合、JuMPはすべての定数項を制約の右辺に集約するため、関数を修正するのではなく、集合は`-value`によって変換されます。例えば、制約`2x <= 3`がある場合、`add_to_function_constant(c, 4)`はそれを`2x <= -1`に修正します。

## 例

スカラー制約の場合、集合は`-value`によって変換されます：

```jldoctest; setup = :(using JuMP; model = Model(); @variable(model, x)), filter=r"≤|<="
julia> @constraint(model, con, 0 <= 2x - 1 <= 2)
con : 2 x ∈ [1.0, 3.0]

julia> add_to_function_constant(con, 4)

julia> con
con : 2 x ∈ [-3.0, -1.0]
```

ベクトル制約の場合、定数は関数に追加されます：

```jldoctest; setup = :(using JuMP; model = Model(); @variable(model, x); @variable(model, y)), filter=r"≤|<="
julia> @constraint(model, con, [x + y, x, y] in SecondOrderCone())
con : [x + y, x, y] ∈ MathOptInterface.SecondOrderCone(3)

julia> add_to_function_constant(con, [1, 2, 2])

julia> con
con : [x + y + 1, x + 2, y + 2] ∈ MathOptInterface.SecondOrderCone(3)
```
