```
iscomplete(grammar::AbstractGrammar, node::RuleNode)
```

Returns true if the expression represented by the [`RuleNode`](@ref) is a complete expression,  meaning that it is fully defined and doesn't have any [`Hole`](@ref)s.
