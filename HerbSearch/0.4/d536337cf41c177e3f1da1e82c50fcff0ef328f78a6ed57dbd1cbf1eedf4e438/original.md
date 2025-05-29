```
heuristic_smallest_domain(node::AbstractRuleNode, max_depth::Int)::Union{ExpandFailureReason, HoleReference}
```

Defines a heuristic over all available holes in the unfinished AST, by considering the size of their respective domains. A domain here describes the number of possible derivations with respect to the constraints. Returns a [`HoleReference`](@ref) once a hole is found. 
