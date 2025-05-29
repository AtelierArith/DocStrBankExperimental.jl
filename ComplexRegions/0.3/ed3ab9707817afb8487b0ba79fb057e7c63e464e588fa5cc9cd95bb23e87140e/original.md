```
isapprox(C1::Circle,C2::Circle; tol=<default>)
C1 ≈ C2
```

Determine if `C1` and `C2` represent the same circle, irrespective of the type or values of its parameters. Identity is determined by agreement within `tol`, which is interpreted as the weaker of absolute and relative differences.
