```
DebugGradient <: DebugAction
```

debug for the gradient evaluated at the current iterate

# Constructors

```
DebugGradient(; long=false, prefix= , format= "$prefix%s", io=stdout)
```

display the short (`false`) or long (`true`) default text for the gradient, or set the `prefix` manually. Alternatively the complete format can be set.
