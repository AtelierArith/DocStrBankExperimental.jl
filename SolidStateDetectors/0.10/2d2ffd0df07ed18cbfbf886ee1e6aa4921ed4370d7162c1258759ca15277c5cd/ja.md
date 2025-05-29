```
struct ElectricField{T, N, S, AT} <: AbstractArray{T, N}
```

シミュレーションの電場（ボルト毎メートル (V/m) 単位）。

## パラメトリック型

  * `T`: `grid.axes` の要素型。
  * `N`: `grid` と `data` 配列の次元。
  * `S`: 座標系（`Cartesian` または `Cylindrical`）。
  * `AT`: 軸の型。

## フィールド

  * `data::Array{<:StaticArray{Tuple{N}, T}, N}`: `grid` の離散点での電場ベクトルを含む配列。
  * `grid::Grid{T, N, S, AT}`: 電場が決定される離散点を定義する [`Grid`](@ref)。
