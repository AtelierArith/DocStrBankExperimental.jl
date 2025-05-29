```
reduced_cost(x::GenericVariableRef{T})::T where {T}
```

変数 `x` に関連する削減コストを返します。

削減コストの一つの解釈は、変数の境界を無限小だけ緩和したときの目的関数の変化です。

このメソッドは、アクティブな変数境界のシャドウプライスを照会することと同等です（存在し、アクティブである場合）。

参照: [`shadow_price`](@ref)。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x <= 1);

julia> @objective(model, Max, 2 * x + 1);

julia> optimize!(model)

julia> dual_status(model)
FEASIBLE_POINT::ResultStatusCode = 1

julia> reduced_cost(x)
2.0
```
