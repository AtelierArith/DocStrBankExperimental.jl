```
isterminal(rule::Any, types::AbstractVector{Symbol})
```

Returns true if the rule is terminal, ie does not contain any of the types in the provided vector. For example, :(x) is terminal, and :(1+1) is terminal, but :(Real + Real) is typically not.
