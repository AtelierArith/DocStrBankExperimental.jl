```
DebugWarnIfFieldNotFinite <: DebugAction
```

A debug to see when a field from the options is not finite, for example `Inf` or `Nan`

# Constructor

```
DebugWarnIfFieldNotFinite(field::Symbol, warn=:Once)
```

Initialize the warning to warn `:Once`.

This can be set to `:Once` to only warn the first time the cost is Nan. It can also be set to `:No` to deactivate the warning, but this makes this Action also useless. All other symbols are handled as if they were `:Always:`

# Example

```
DebugWaranIfFieldNotFinite(:Gradient)
```

Creates a [`DebugAction`] to track whether the gradient does not get `Nan` or `Inf`.
