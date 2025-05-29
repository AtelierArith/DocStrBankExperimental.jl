```
Polar(ρ, ϕ)
Polar{Datum}(ρ, ϕ)
```

半径 `ρ ∈ [0,∞)` の極座標（単位はデフォルトでメートル）、角度 `ϕ ∈ [0,2π)` の角度単位（デフォルトでラジアン）および指定された `Datum`（デフォルトは `NoDatum`）です。

## 例

```julia
Polar(1, π/4) # デフォルトの単位を追加
Polar(1m, (π/4)rad) # 整数は浮動小数点数に変換される
Polar(1.0m, 45°) # 度はラジアンに変換される
Polar(1.0km, (π/4)rad)
Polar{WGS84Latest}(1.0m, (π/4)rad)
```

## 参考文献

  * [極座標系](https://en.wikipedia.org/wiki/Polar_coordinate_system)
  * [ISO 80000-2:2019](https://www.iso.org/standard/64973.html)
  * [ISO 80000-3:2019](https://www.iso.org/standard/64974.html)
