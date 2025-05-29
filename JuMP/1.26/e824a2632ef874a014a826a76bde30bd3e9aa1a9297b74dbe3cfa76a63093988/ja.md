```
set_normalized_rhs(
    constraints::AbstractVector{<:ConstraintRef},
    values::AbstractVector{<:Number}
)
```

すべての `constraints` の右辺項を `values` に設定します。

このステップの前に、JuMP はすべての定数項を制約の右辺に集約します。たとえば、制約 `2x + 1 <= 2` がある場合、`set_normalized_rhs([con], [4])` は制約 `2x <= 4` を作成し、`2x + 1 <= 4` にはなりません。

## 例

```jldoctest; filter=r"≤|<="
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, con1, 2x + 1 <= 2)
con1 : 2 x ≤ 1

julia> @constraint(model, con2, 3x + 2 <= 4)
con2 : 3 x ≤ 2

julia> set_normalized_rhs([con1, con2], [4, 5])

julia> con1
con1 : 2 x ≤ 4

julia> con2
con2 : 3 x ≤ 5
```
