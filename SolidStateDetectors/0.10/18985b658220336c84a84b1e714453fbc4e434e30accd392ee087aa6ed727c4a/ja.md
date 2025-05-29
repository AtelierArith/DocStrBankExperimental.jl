```
struct PointTypes{T, N, S, AT} <: AbstractArray{T, N}
```

[`ElectricPotential`](@ref)を計算するために使用されるグリッドポイントに関する情報がビットフラグを介して保存されています。データは`UInt8`の[`PointType`](@ref)として保存されています。

## パラメトリック型

  * `T`: `grid.axes`の要素型。
  * `N`: `grid`および`data`配列の次元。
  * `S`: 座標系（`Cartesian`または`Cylindrical`）。
  * `AT`: 軸の型。

## フィールド

  * `data::Array{PointType, N}`: `grid`の離散点におけるポイントタイプの値を含む配列。
  * `grid::Grid{T, N, S, AT}`: ポイントタイプが決定される離散点を定義する[`Grid`](@ref)。

さらに[`PointType`](@ref)も参照してください。
