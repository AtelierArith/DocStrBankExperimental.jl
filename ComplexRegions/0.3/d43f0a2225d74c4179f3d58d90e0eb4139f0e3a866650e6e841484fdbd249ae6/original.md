```
isapprox(A1::Arc,A2::Arc; tol=<default>)
A1 ≈ A2
```

Determine if `A1` and `A2` represent the same arc, irrespective of the type or values of its parameters. Identity is determined by agreement within `tol`, which is interpreted as the weaker of absolute and relative differences.
