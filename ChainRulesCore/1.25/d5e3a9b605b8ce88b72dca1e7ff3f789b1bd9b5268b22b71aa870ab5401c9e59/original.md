```
zero_tangent(primal)
```

This returns an appropriate zero tangent suitable for accumulating tangents of the primal. For mutable composites types this is a structural [`MutableTangent`](@ref) For `Array`s, it is applied recursively for each element. For other types, in particular immutable types, we do not make promises beyond that it will be `iszero` and suitable for accumulating against. For types without a tangent space (e.g. singleton structs) this returns `NoTangent()`. In general, it is more likely to produce a structural tangent.

!!! warning "Exprimental"
    `zero_tangent`is an experimental feature, and is part of the mutation support featureset. While this notice remains it may have changes in behavour, and interface in any *minor* version of ChainRulesCore. Exactly how it should be used (e.g. is it forward-mode only?)

