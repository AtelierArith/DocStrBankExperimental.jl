```
abstract type AbstractGrammarConstraint <: AbstractConstraint
```

Abstract type representing all user-defined constraints. Each grammar constraint has a related [AbstractLocalConstraint](@ref) that is responsible for propagating the constraint at a specific location in the tree. Grammar constraints should implement `on_new_node` to post a [`AbstractLocalConstraint`](@ref) at that new node
