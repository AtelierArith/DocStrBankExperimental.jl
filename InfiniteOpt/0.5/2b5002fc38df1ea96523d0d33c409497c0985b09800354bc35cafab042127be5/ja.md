```
JuMP.add_bridge(model::InfiniteModel,
                BridgeType::Type{<:MOI.Bridges.AbstractBridge})
```

`JuMP.add_bridge`を拡張して、`BridgeType`を最適化モデルがサポートされていない制約を最適化によってサポートされている制約のみを使用して同等の定式化に変換するために使用できるブリッジのリストに追加します。
