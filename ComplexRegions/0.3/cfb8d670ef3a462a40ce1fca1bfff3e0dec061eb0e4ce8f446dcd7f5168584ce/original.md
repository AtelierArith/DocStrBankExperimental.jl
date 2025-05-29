```
isapprox(R1::Ray, R2::Ray; tol=<default>)
R1 ≈ R2
```

Determine if `R1` and `R2` represent the same segment, irrespective of the type or values of its parameters. Identity is determined by agreement within `tol`, which is interpreted as the weaker of absolute and relative differences.
