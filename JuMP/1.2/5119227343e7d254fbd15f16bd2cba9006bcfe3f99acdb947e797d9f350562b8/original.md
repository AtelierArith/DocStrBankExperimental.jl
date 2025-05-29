```
 add_bridge(model::Model,
            BridgeType::Type{<:MOI.Bridges.AbstractBridge})
```

Add `BridgeType` to the list of bridges that can be used to transform unsupported constraints into an equivalent formulation using only constraints supported by the optimizer.
