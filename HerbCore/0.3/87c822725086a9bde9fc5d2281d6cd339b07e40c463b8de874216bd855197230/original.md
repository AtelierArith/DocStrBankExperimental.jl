```
abstract type AbstractRuleNode end
```

Abstract type for representing expression trees. An `AbstractRuleNode` is expected to implement the following functions:

  * `isfilled(::AbstractRuleNode)::Bool`. True iff the grammar rule this node holds is not ambiguous, i.e. has domain size 1.
  * `isuniform(::AbstractRuleNode)::Bool`. True iff the children of this node are known.
  * `get_rule(::AbstractRuleNode)::Int`. Returns the index of the grammar rule it represents.
  * `get_children(::AbstractRuleNode)::Vector{AbstractRuleNode}`. Returns the children of this node.

Expression trees consist of [`RuleNode`](@ref)s and [`AbstractHole`](@ref)s.

  * A [`RuleNode`](@ref) represents a certain production rule in the [`AbstractGrammar`](@ref).
  * A [`AbstractHole`](@ref) is a placeholder where certain rules in the grammar still can be applied.
