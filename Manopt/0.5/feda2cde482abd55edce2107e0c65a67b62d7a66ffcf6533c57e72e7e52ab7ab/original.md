```
DebugWarnIfCostIncreases <: DebugAction
```

print a warning if the cost increases.

Note that this provides an additional warning for gradient descent with its default constant step size.

# Constructor

```
DebugWarnIfCostIncreases(warn=:Once; tol=1e-13)
```

Initialize the warning to warning level (`:Once`) and introduce a tolerance for the test of `1e-13`.

The `warn` level can be set to `:Once` to only warn the first time the cost increases, to `:Always` to report an increase every time it happens, and it can be set to `:No` to deactivate the warning, then this [`DebugAction`](@ref) is inactive. All other symbols are handled as if they were `:Always:`
