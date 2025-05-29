```
struct EffectiveChargeDensity{T, N, S, AT} <: AbstractArray{T, N}
```

電気ポテンシャルを計算するために必要な効果的電荷密度は、電荷密度（C/m³）とそれぞれのグリッドポイントのボクセルの体積（m³）を掛けたものです。したがって、効果的電荷密度の単位はクーロン（C）です。

## パラメトリック型

  * `T`: `data`の要素型。
  * `N`: `grid`および`data`配列の次元。
  * `S`: 座標系（`Cartesian`または`Cylindrical`）。
  * `AT`: 軸の型。

## フィールド

  * `data::Array{T, N}`: `grid`の離散点における効果的電荷密度の値を含む配列。
  * `grid::Grid{T, N, S, AT}`: 電気ポテンシャルが決定される離散点を定義する[`Grid`](@ref)。
