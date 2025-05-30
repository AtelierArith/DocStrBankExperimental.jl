```
node_count(model::GenericModel)
```

利用可能な場合、混合整数プログラムにおける最近の最適化中に探索された分岐および境界ノードの総数を返します（[`MOI.NodeCount`](@ref) 属性）。

属性がソルバーによって実装されていない場合、`MOI.GetAttributeNotAllowed` エラーがスローされます。

## 例

```jldoctest; filter=r"[0-9].+"
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> optimize!(model)

julia> node_count(model)
0
```
