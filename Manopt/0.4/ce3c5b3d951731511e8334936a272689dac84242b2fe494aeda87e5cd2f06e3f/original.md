```
DebugWarnIfCostNotFinite <: DebugAction
```

A debug to see when a field (value or array within the AbstractManoptSolverState is or contains values that are not finite, for example `Inf` or `Nan`.

# Constructor

```
DebugWarnIfCostNotFinite(field::Symbol, warn=:Once)
```

Initialize the warning to warn `:Once`.

This can be set to `:Once` to only warn the first time the cost is Nan. It can also be set to `:No` to deactivate the warning, but this makes this Action also useless. All other symbols are handled as if they were `:Always:`
