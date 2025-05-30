```
StructuralTangent{P} <: AbstractTangent
```

Representing the type of the tangent of a `struct` `P` (or a `Tuple`/`NamedTuple`). as an object with mirroring fields.

!!! warning "Exprimental"
    `StructuralTangent` is an experimental feature, and is part of the mutation support featureset. The `StructuralTangent` constructor returns a `MutableTangent` for mutable structs. `MutableTangent` is an experimental feature. Thus use of `StructuralTangent` (rather than `Tangent` directly) is also experimental. While this notice remains it may have changes in behavour, and interface in any *minor* version of ChainRulesCore.

