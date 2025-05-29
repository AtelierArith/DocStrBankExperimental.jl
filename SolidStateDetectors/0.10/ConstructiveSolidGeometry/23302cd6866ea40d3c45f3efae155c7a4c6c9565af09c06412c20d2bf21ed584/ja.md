```
struct CylindricalPoint{T} <: AbstractCoordinatePoint{T, Cylindrical}
```

円筒座標系における三次元点を表します。

## フィールド

  * `r`: 半径（m単位）。
  * `φ`: 極角（ラジアン単位）。
  * `z`: `z`座標（m単位）。

!!! note
    `φ == 0` はデカルト座標系の `x` 軸に対応します。


関連情報として [`CartesianPoint`](@ref) を参照してください。
