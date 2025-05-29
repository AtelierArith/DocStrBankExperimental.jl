```
start_value(con_ref::ConstraintRef)
```

制約 `con_ref` の原始開始値 ([`MOI.ConstraintPrimalStart`](@ref)) を返します。

原始開始値が設定されていない場合、`start_value` は `nothing` を返します。

他にも [`set_start_value`](@ref) を参照してください。

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
