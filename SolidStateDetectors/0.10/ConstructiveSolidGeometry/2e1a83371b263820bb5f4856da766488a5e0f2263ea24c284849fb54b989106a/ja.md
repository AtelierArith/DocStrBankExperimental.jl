```
struct CartesianVector{T} <: AbstractCoordinateVector{T, Cartesian}
```

デカルト座標系における三次元ベクトルを表します。

## フィールド

  * `x`: x座標（m単位）。
  * `y`: y座標（m単位）。
  * `z`: z座標（m単位）。

関連項目として[`CylindricalVector`](@ref)を参照してください。
