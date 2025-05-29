```
 add_bridge(model::Model,
            BridgeType::Type{<:MOI.Bridges.AbstractBridge})
```

`BridgeType`を、最適化ツールによってサポートされている制約のみを使用して、サポートされていない制約を同等の定式化に変換するために使用できる橋のリストに追加します。
