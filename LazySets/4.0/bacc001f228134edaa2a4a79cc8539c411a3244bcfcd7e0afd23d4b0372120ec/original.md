# Extended help

```
isuniversal(P::AbstractPolyhedron, [witness]::Bool=false)
```

### Algorithm

`P` is universal iff it has no constraints.

A witness is produced using `isuniversal(H)` where `H` is the first linear constraint of `P`.
