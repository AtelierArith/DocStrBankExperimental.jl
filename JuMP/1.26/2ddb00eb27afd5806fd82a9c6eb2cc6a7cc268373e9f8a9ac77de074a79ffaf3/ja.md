```
bridge_constraints(model::GenericModel)
```

直接モードの場合、`false`を返します。

手動または自動モードの場合、最適化ツールが設定されているかどうかを示す`Bool`を返し、適切な変換が利用可能な場合にサポートされていない制約が自動的に同等のサポートされている制約にブリッジされるかどうかを示します。

## 例

```jldoctest
julia> import Ipopt

julia> model = Model(Ipopt.Optimizer);

julia> bridge_constraints(model)
true

julia> model = Model(Ipopt.Optimizer; add_bridges = false);

julia> bridge_constraints(model)
false
```
