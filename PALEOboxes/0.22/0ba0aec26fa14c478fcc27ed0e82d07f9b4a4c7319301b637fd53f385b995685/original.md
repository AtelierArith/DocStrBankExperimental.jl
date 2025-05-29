```
zero_ad(x...) -> 0.0*x
```

Provide a zero of type of `x` (or type of `x1*x2*...` if given multiple arguments), retaining AD dependency information.

Workaround to enable use of conditional logic whilst retaining dependency information for tracing Jacobian sparsity pattern.
