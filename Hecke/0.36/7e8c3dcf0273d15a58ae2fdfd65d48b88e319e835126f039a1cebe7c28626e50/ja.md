```
coordinates(x::AlgAssAbsOrdElem; copy::Bool = true) -> Vector{ZZRingElem}
coordinates(x::AlgAssRelOrdElem; copy::Bool = true) -> Vector{NumFieldElem}
```

`parent(x)`の基底における$x$の座標を返します。
