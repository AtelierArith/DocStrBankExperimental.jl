```
JuMP.add_bridge(model::InfiniteModel,
                BridgeType::Type{<:MOI.Bridges.AbstractBridge})
```

Extend `JuMP.add_bridge` to add `BridgeType` to the list of bridges that can be used by the optimizer model to transform unsupported constraints into an equivalent formulation using only constraints supported by the optimizer.
