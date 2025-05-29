```
set_start_value(con_ref::ConstraintRef, value)
```

制約 `con_ref` のプライマルスタート値 ([`MOI.ConstraintPrimalStart`](@ref)) を `value` に設定します。

プライマルスタート値を削除するには、`nothing` に設定します。

詳細は [`start_value`](@ref) を参照してください。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, start = 2.0);

julia> @constraint(model, c, [2x] in Nonnegatives())
c : [2 x] ∈ Nonnegatives()

julia> set_start_value(c, [4.0])

julia> start_value(c)
1-element Vector{Float64}:
 4.0

julia> set_start_value(c, nothing)

julia> start_value(c)
```
