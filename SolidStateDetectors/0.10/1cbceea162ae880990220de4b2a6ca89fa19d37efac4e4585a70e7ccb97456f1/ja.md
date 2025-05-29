```
struct Grid{T, N, S <: AbstractCoordinateSystem, AT} <: AbstractGrid{T, N}
```

グリッドの次元を定義する `N` 軸のコレクションで、[`ElectricPotential`](@ref)、[`ElectricField`](@ref) または [`WeightingPotential`](@ref) を計算するために必要です。

## パラメトリック型

  * `T`: 軸のティックタイプ（要素タイプ）。
  * `N`: グリッドの次元。
  * `S`: 座標系（`Cartesian` または `Cylindrical`）。
  * `AT`: 軸のタイプ。

## フィールド

  * `axes::AT`: グリッドの各次元に対する `DiscreteAxis` を含む長さ `N` のタプル。

詳細は [`DiscreteAxis`](@ref) を参照してください。
