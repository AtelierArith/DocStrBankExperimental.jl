```
solve_time(model::GenericModel)
```

利用可能な場合、ソルバーによって報告された壁時計秒での解決時間（[`MOI.SolveTimeSec`](@ref) 属性）を返します。

属性がソルバーによって実装されていない場合、`MOI.GetAttributeNotAllowed` エラーをスローします。

## 例

```jldoctest; filter=r"[0-9].+"
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> optimize!(model)

julia> solve_time(model)
1.0488089174032211e-5
```
