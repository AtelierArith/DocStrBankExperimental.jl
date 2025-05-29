```
struct CartesianPoint{T} <: AbstractCoordinatePoint{T, Cartesian}
```

デカルト座標系における三次元点を表します。

## フィールド

  * `x`: x座標（m単位）。
  * `y`: y座標（m単位）。
  * `z`: z座標（m単位）。

関連項目として[`CylindricalPoint`](@ref)を参照してください。
