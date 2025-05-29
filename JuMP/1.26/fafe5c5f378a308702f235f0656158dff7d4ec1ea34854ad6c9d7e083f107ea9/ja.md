```
has_duals(model::GenericModel; result::Int = 1)
```

結果インデックス `result` でクエリ可能な双対解がソルバーに存在する場合は `true` を返し、そうでない場合は `false` を返します。

[`dual`](@ref)、[`shadow_price`](@ref)、および [`result_count`](@ref) も参照してください。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x);

julia> @constraint(model, c, x <= 1)
c : x ≤ 1

julia> @objective(model, Max, 2 * x + 1);

julia> has_duals(model)
false

julia> optimize!(model)

julia> has_duals(model)
true
```
