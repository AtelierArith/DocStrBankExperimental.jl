```
relative_gap(model::GenericModel)
```

`optimize!(model)` を呼び出した後の最終的な相対最適性ギャップを返します。

正確な値は、最適化に使用される特定のソルバーによる [`MOI.RelativeGap`](@ref) の実装に依存します。

この関数は、[`MOI.RelativeGap`](@ref) 属性を照会することと同等です。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 1, Int);

julia> @objective(model, Min, 2 * x + 1);

julia> optimize!(model)

julia> relative_gap(model)
0.0
```
