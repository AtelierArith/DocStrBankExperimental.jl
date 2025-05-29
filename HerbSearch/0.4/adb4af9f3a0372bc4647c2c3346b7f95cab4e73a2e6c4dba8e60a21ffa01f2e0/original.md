```
heuristic_leftmost(node::AbstractRuleNode, max_depth::Int)::Union{ExpandFailureReason, HoleReference}
```

Defines a heuristic over holes, where the left-most hole always gets considered first. Returns a [`HoleReference`](@ref) once a hole is found. This is the default option for enumerators.
