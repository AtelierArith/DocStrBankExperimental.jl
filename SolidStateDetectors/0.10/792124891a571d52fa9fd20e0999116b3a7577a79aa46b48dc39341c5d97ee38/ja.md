```
struct WeightingPotential{T, N, S, AT} <: AbstractArray{T, N}
```

与えられた [`Contact`](@ref) のための重み付けポテンシャルで、単位のないポテンシャルです。

## パラメトリック型

  * `T`: `data` の要素型。
  * `N`: `grid` と `data` 配列の次元。
  * `S`: 座標系（`Cartesian` または `Cylindrical`）。
  * `AT`: 軸の型。

## フィールド

  * `data::Array{T, N}`: `grid` の離散点での重み付けポテンシャルの値を含む配列。
  * `grid::Grid{T, N, S, AT}`: 重み付けポテンシャルが決定される離散点を定義する [`Grid`](@ref)。
