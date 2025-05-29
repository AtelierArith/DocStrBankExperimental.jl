```
RuleNode(ind::Int, _val::Any)
```

Create a [`RuleNode`](@ref) for the [`AbstractGrammar`](@ref) rule with index `ind`,  `_val` as immediately evaluated value and no children

!!! warning
    Only use this constructor if you are absolutely certain that a rule is terminal and cannot have children. Use [`RuleNode(ind::Int, grammar::AbstractGrammar)`] for rules that might have children. In general, [`AbstractHole`](@ref)s should be used as a placeholder when the children of a node are not yet known.


!!! compat
    Evaluate immediately functionality is not yet supported by most of Herb.jl.

