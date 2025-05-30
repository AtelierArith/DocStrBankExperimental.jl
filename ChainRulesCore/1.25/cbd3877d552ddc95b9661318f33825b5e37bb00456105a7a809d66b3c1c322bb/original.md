```
MutableTangent{P}(fields) <: StructuralTangent{P} <: AbstractTangent
```

This type represents the tangent to a mutable struct. It itself is also mutable.

!!! warning "Exprimental"
    MutableTangent is an experimental feature, and is part of the mutation support featureset. While this notice remains it may have changes in behavour, and interface in any *minor* version of ChainRulesCore. Exactly how it should be used (e.g. is it forward-mode only?)


!!! warning "Do not directly mess with the tangent backing data"
    It is relatively straight forward for a forwards-mode AD to work correctly in the presence of mutation and aliasing of primal values. However, this requires that the tangent is aliased in turn and conversely that it is copied when the primal is). If you seperately alias the backing data, etc by using the internal `ChainRulesCore.backing` function you can break this.

