```
isapprox(L1::Line, L2::Line; tol=<default>)
L1 ≈ L2
```

Determine if `L1` and `L2` represent the same line, irrespective of the type or values of its parameters. Identity is determined by agreement within `tol`, which is interpreted as the weaker of absolute and relative differences.
