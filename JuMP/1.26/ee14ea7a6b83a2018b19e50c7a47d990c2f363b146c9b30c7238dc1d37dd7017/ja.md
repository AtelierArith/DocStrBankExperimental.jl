```
set_dual_start_value(con_ref::ConstraintRef, value)
```

制約 `con_ref` の双対開始値 (MOI 属性 `ConstraintDualStart`) を `value` に設定します。

双対開始値を削除するには、それを `nothing` に設定します。

詳細は [`dual_start_value`](@ref) を参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, start = 2.0);

julia> @constraint(model, c, [2x] in Nonnegatives())
c : [2 x] ∈ Nonnegatives()

julia> set_dual_start_value(c, [0.0])

julia> dual_start_value(c)
1-element Vector{Float64}:
 0.0

julia> set_dual_start_value(c, nothing)

julia> dual_start_value(c)
```
