```
heuristic_rightmost(node::AbstractRuleNode, max_depth::Int)::Union{ExpandFailureReason, HoleReference}
```

Defines a heuristic over holes, where the right-most hole always gets considered first. Returns a [`HoleReference`](@ref) once a hole is found. 
