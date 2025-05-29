```julia
struct DirichletBC{U} <: IncompressibleNavierStokes.AbstractBC
```

速度のためのディリクレ境界条件、ここで `u[1] = (x..., t) -> u1_BC` から `u[d] = (x..., t) -> ud_BC` まで、`d` は次元です。

`u` が `nothing` の場合、境界条件はすべての速度成分がゼロであるノースリップ境界条件です。

## フィールド

  * `u`: 境界条件
