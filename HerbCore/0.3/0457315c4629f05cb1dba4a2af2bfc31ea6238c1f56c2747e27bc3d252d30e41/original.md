```
RuleNode <: AbstractRuleNode
```

A [`RuleNode`](@ref) represents a node in an expression tree. Each node corresponds to a certain rule in the [`AbstractGrammar`](@ref). A [`RuleNode`](@ref) consists of:

  * `ind`: The index of the rule in the [`AbstractGrammar`](@ref) which this node is representing.
  * `_val`: Field for caching evaluations of `RuleNode`s, preventing multiple unnecessary evaluations. The field can be used to store any needed infromation.
  * `children`: The children of this node in the expression tree

!!! compat
    Evaluate immediately functionality is not yet supported by most of Herb.jl.

