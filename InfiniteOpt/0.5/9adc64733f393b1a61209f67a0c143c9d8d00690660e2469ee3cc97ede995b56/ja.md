```
JuMP.bridge_constraints(model::InfiniteModel)::Bool
```

`JuMP.bridge_constraints`を拡張して、無限モデル`model`がオプティマイザモデルを持ち、オプティマイザが設定されている場合に、サポートされていない制約が適切な変換が利用可能なときに自動的に同等のサポートされている制約にブリッジされるかどうかを返すようにします。

**例**

```julia-repl
julia> bridge_constraints(model)
false
```
