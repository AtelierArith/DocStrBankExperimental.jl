```
contains_hole(rn::RuleNode) = any(contains_hole(c) for c ∈ rn.children)
```

Checks if an [`AbstractRuleNode`](@ref) tree contains a [`AbstractHole`](@ref).
