```julia
Lattice(
    height::Int64,
    max_height::Int64,
    min_height::Int64
) -> ActinRingsMC.Lattice

```

yに周期的条件を持つ2D格子。

最大および最小の高さは、足場フィラメントの数とフィラメントの長さに基づいて計算されるべきです。
