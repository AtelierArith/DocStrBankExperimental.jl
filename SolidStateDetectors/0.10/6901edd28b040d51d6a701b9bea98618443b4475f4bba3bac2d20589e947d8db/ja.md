```
struct ElectricPotential{T, N, S, AT} <: AbstractArray{T, N}
```

シミュレーションの電位（ボルト (V) 単位）。

## パラメトリック型

  * `T`: `data`の要素型。
  * `N`: `grid`および`data`配列の次元。
  * `S`: 座標系（`Cartesian`または`Cylindrical`）。
  * `AT`: 軸の型。

## フィールド

  * `data::Array{T, N}`: `grid`の離散点での電位の値を含む配列。
  * `grid::Grid{T, N, S, AT}`: [`Grid`](@ref) は電位が決定される離散点を定義します。
