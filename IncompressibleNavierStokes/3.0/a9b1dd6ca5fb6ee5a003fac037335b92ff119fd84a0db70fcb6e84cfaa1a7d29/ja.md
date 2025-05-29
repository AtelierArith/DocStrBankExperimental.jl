```julia
struct SymmetricBC <: IncompressibleNavierStokes.AbstractBC
```

対称境界条件。境界の両側で平行速度と圧力は同じです。法線速度はゼロです。

## フィールド
