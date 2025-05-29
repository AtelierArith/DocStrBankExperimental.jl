```
get_variables(method::AbstractReactionMethod; filterfn = v -> true) -> Vector{VariableReaction}
```

Get VariableReactions from `method.varlists` as a flat Vector, optionally restricting to those that match `filterfn`
