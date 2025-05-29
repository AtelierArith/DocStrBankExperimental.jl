```
objective_bound(model::GenericModel)
```

`optimize!(model)` を呼び出した後の最適目的値に関する最良の既知の境界を返します。

スカラー値の目的の場合、この関数は `Float64` を返します。ベクトル値の目的の場合、`Vector{Float64}` を返します。

ベクトル値の目的の場合、これは *理想点* を返します。つまり、各目的が独立に最適化された場合に得られる点です。

この関数は [`MOI.ObjectiveBound`](@ref) 属性を照会することと同等です。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 1, Int);

julia> @objective(model, Min, 2 * x + 1);

julia> optimize!(model)

julia> objective_bound(model)
3.0
```
