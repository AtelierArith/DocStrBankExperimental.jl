```
TimeDerivative(variable, expression [, τ])
```

The second simplest process that equates the time derivative of the `variable` to the given `expression` while providing some conveniences over manually constructing an `Equation`.

It creates the equation `τ_$(variable) Differential(t)(variable) ~ expression` by constructing a new `@parameter` with default value `τ` (if `τ` is already a `@parameter`, it is used as-is). If `τ` is not given, then 1 is used at its place and no parameter is created.

Note that if `iszero(τ)`, then the process `variable ~ expression` is created.
