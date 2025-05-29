```
coordinates(x::AlgAssAbsOrdElem; copy::Bool = true) -> Vector{ZZRingElem}
coordinates(x::AlgAssRelOrdElem; copy::Bool = true) -> Vector{NumFieldElem}
```

Returns the coordinates of $x$ in the basis of `parent(x)`.
