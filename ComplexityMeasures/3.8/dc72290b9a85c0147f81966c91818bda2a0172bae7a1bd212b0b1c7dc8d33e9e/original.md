```
probabilities!(s, args...)
```

Similar to `probabilities(args...)`, but allows pre-allocation of temporarily used containers `s`.

Only works for certain estimators. See for example [`OrdinalPatterns`](@ref).
