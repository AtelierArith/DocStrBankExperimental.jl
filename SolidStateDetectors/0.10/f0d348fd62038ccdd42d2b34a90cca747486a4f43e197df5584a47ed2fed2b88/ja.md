```
struct DielectricDistribution{T, N, S, AT} <: AbstractArray{T, N}
```

誘電体分布、または相対誘電率の分布、$\epsilon_r$、は[`ElectricPotential`](@ref)を計算するために必要です。誘電体分布は無次元です。

## パラメトリック型

  * `T`: `data`の要素型。
  * `N`: `grid`および`data`配列の次元。
  * `S`: 座標系（`Cartesian`または`Cylindrical`）。
  * `AT`: 軸の型。

## フィールド

  * `data::Array{T, N}`: `grid`の離散点における誘電体分布の値を含む配列。
  * `grid::Grid{T, N, S, AT}`: 電気ポテンシャルが決定される離散点を定義する[`Grid`](@ref)。

!!! note
    `data`配列は、`grid`の拡張グリッドの軸目盛りによって定義された点の間の離散点における誘電体分布の値を含みます。

    したがって、`size(data) == size(grid) .+ 1` !

