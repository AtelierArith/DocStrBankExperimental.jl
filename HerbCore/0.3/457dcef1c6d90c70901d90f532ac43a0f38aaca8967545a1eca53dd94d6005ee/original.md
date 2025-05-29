```
isfilled(node::AbstractRuleNode)::Bool
```

Returns whether the [`AbstractRuleNode`] holds a single rule. This is always the case for [`RuleNode`](@ref)s. Holes are considered to be "filled" iff their domain size is exactly 1.
