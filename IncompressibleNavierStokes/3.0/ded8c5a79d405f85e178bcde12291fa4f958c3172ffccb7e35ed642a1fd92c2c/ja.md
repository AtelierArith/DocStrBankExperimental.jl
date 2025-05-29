```julia
struct PressureBC <: IncompressibleNavierStokes.AbstractBC
```

圧力境界条件。圧力は境界（通常は「出口」）で指定されます。速度はゼロのノイマン条件を持ちます。

注：現在、圧力は全境界で定数値のゼロとして指定されています。

## フィールド
