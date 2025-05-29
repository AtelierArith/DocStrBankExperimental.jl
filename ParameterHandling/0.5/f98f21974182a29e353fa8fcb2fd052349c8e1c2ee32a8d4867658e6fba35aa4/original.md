```
positive(val::Real, transform=exp, ε=sqrt(eps(typeof(val))))
```

Return a `Positive`. The `value` of a `Positive` is a `Real` number that is constrained to be positive. This is represented in terms of a `transform` that maps an `unconstrained_value` to the positive reals. Satisfies `val ≈ transform(unconstrained_value)`.
