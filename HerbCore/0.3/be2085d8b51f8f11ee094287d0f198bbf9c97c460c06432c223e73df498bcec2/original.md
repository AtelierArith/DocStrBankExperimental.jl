```
AbstractHole <: AbstractRuleNode
```

A [`AbstractHole`](@ref) is a placeholder where certain rules from the grammar can still be applied. The `domain` of a [`AbstractHole`](@ref) defines which rules can be applied. The `domain` is a bitvector, where the `i`th bit is set to true if the `i`th rule in the grammar can be applied.
