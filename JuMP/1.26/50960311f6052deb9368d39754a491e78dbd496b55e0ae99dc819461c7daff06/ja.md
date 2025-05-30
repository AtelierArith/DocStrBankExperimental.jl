```
simplex_iterations(model::GenericModel)
```

利用可能な場合、最も最近の最適化中の累積単体法反復回数（[`MOI.SimplexIterations`](@ref) 属性）を返します。

属性がソルバーによって実装されていない場合、`MOI.GetAttributeNotAllowed` エラーが発生します。

## 例

```jldoctest; filter=r"[0-9].+"
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> optimize!(model)

julia> simplex_iterations(model)
0
```
