```
Spherical(r, θ, ϕ)
Spherical{Datum}(r, θ, ϕ)
```

半径 `r ∈ [0,∞)` の球面座標（単位はデフォルトでメートル）、極角 `θ ∈ [0,π]` および方位角 `ϕ ∈ [0,2π)`（単位はデフォルトでラジアン）と指定された `Datum`（デフォルトは `NoDatum`）です。

## 例

```julia
Spherical(1, π/4, π/4) # デフォルトの単位を追加
Spherical(1m, (π/4)rad, (π/4)rad) # 整数は浮動小数点数に変換されます
Spherical(1.0m, 45°, 45°) # 度はラジアンに変換されます
Spherical(1.0km, (π/4)rad, (π/4)rad)
Spherical{WGS84Latest}(1.0m, (π/4)rad, (π/4)rad)
```

## 参考文献

  * [球面座標系](https://en.wikipedia.org/wiki/Spherical_coordinate_system)
  * [ISO 80000-2:2019](https://www.iso.org/standard/64973.html)
  * [ISO 80000-3:2019](https://www.iso.org/standard/64974.html)
