```
has_values(model::GenericModel; result::Int = 1)
```

結果インデックス `result` でクエリ可能なプライマリ解がソルバーに存在する場合は `true` を返し、そうでない場合は `false` を返します。

[`value`](@ref) と [`result_count`](@ref) も参照してください。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x);

julia> @constraint(model, c, x <= 1)
c : x ≤ 1

julia> @objective(model, Max, 2 * x + 1);

julia> has_values(model)
false

julia> optimize!(model)

julia> has_values(model)
true
```
