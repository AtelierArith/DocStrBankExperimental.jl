```
dual_objective_value(model::GenericModel; result::Int = 1)
```

最も最近ソルバーによって返された解の結果インデックス `result` に関連付けられた双対問題の目的値を返します。

ソルバーがこの属性をサポートしていない場合、`MOI.UnsupportedAttribute{MOI.DualObjectiveValue}` がスローされます。

この関数は、[`MOI.DualObjectiveValue`](@ref) 属性をクエリすることと同等です。

関連情報: [`result_count`](@ref)。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 1);

julia> @objective(model, Min, 2 * x + 1);

julia> optimize!(model)

julia> dual_objective_value(model)
3.0

julia> dual_objective_value(model; result = 2)
ERROR: Result index of attribute MathOptInterface.DualObjectiveValue(2) out of bounds. There are currently 1 solution(s) in the model.
Stacktrace:
[...]
```
