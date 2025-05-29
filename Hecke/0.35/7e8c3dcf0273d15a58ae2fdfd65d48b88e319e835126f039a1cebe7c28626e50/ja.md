```
coordinates(x::AlgAssAbsOrdElem; copy::Bool = true) -> Vector{ZZRingElem}
coordinates(x::AlgAssRelOrdElem; copy::Bool = true) -> Vector{NumFieldElem}
```

$$
x
$$

の`parent(x)`の基底における座標を返します。
