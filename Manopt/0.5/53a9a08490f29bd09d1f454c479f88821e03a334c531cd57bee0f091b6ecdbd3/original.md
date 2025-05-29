```
DebugGradientNorm <: DebugAction
```

debug for gradient evaluated at the current iterate.

# Constructors

```
DebugGradientNorm([long=false,p=print])
```

display the short (`false`) or long (`true`) default text for the gradient norm.

```
DebugGradientNorm(prefix[, p=print])
```

display the a `prefix` in front of the gradient norm.
