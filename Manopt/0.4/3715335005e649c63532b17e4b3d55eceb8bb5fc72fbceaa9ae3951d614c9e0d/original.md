```
DebugWarnIfLagrangeMultiplierIncreases <: DebugAction
```

print a warning if the Lagrange parameter based value $-ξ$ of the bundle method increases.

# Constructor

```
DebugWarnIfLagrangeMultiplierIncreases(warn=:Once; tol=1e2)
```

Initialize the warning to warning level (`:Once`) and introduce a tolerance for the test of `1e2`.

The `warn` level can be set to `:Once` to only warn the first time the cost increases, to `:Always` to report an increase every time it happens, and it can be set to `:No` to deactivate the warning, then this [`DebugAction`](@ref) is inactive. All other symbols are handled as if they were `:Always:`
