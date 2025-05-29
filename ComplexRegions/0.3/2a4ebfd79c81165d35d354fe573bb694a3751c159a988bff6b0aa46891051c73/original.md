```
isapprox(S1::Segment,S2::Segment; tol=<default>)
S1 ≈ S2
```

Determine if `S1` and `S2` represent the same segment, irrespective of the type or values of its parameters. Identity is determined by agreement within `tol`, which is interpreted as the weaker of absolute and relative differences.
