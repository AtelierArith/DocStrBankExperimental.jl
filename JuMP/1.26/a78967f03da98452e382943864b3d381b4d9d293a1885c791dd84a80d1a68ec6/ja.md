```
objective_value(model::GenericModel; result::Int = 1)
```

最も最近ソルバーによって返された解の結果インデックス `result` に関連付けられた目的値を返します。

スカラー値の目的の場合、この関数は `Float64` を返します。ベクトル値の目的の場合、`Vector{Float64}` を返します。

この関数は、[`MOI.ObjectiveValue`](@ref) 属性を照会することと同等です。

参照: [`result_count`](@ref).

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 1);

julia> @objective(model, Min, 2 * x + 1);

julia> optimize!(model)

julia> objective_value(model)
3.0

julia> objective_value(model; result = 2)
ERROR: Result index of attribute MathOptInterface.ObjectiveValue(2) out of bounds. There are currently 1 solution(s) in the model.
Stacktrace:
[...]
```
