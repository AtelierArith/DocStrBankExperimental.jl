```
barrier_iterations(model::GenericModel)
```

利用可能な場合、最も最近の最適化中の累積バリア反復回数を返します（[`MOI.BarrierIterations`](@ref) 属性）。

属性がソルバーによって実装されていない場合、`MOI.GetAttributeNotAllowed` エラーがスローされます。

## 例

```jldoctest; filter=r"[0-9].+"
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> optimize!(model)

julia> barrier_iterations(model)
0
```
