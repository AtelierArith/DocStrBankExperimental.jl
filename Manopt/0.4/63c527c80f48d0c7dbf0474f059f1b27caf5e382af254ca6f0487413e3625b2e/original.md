```
AbstractDecoratedManifoldObjective{E<:AbstractEvaluationType,O<:AbstractManifoldObjective}
```

A common supertype for all decorators of [`AbstractManifoldObjective`](@ref)s to simplify dispatch.     The second parameter should refer to the undecorated objective (the most inner one).
