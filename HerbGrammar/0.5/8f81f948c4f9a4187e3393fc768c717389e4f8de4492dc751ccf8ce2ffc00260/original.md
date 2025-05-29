```
cleanup_removed_rules!(g::AbstractGrammar)
```

Removes any placeholders for previously deleted rules.  This means that indices get shifted.

!!! warning
    When indices are shifted, this grammar can no longer be used to interpret  [`AbstractRuleNode`](@ref) trees created before the call to this function. These trees become meaningless.

