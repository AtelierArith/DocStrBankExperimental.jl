```
heuristic_random(node::AbstractRuleNode, max_depth::Int)::Union{ExpandFailureReason, HoleReference}
```

Defines a heuristic over holes, where random holes get chosen randomly using random exploration. Returns a [`HoleReference`](@ref) once a hole is found.
