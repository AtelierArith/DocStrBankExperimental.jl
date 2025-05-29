```
dual(con_ref::ConstraintRef; result::Int = 1)
```

制約 `con_ref` の双対値を、ソルバーによって返された最新の解の結果インデックス `result` に関連付けて返します。

値を要求する前に、[`dual_status`](@ref) を使用して結果が存在するかどうかを確認してください。

関連情報: [`result_count`](@ref), [`shadow_price`](@ref).

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x);

julia> @constraint(model, c, x <= 1)
c : x ≤ 1

julia> @objective(model, Max, 2 * x + 1);

julia> optimize!(model)

julia> dual_status(model)
FEASIBLE_POINT::ResultStatusCode = 1

julia> dual(c)
-2.0
```
