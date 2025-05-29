```
Cylindrical(ρ, ϕ, z)
Cylindrical{Datum}(ρ, ϕ, z)
```

半径 `ρ ∈ [0,∞)` の円柱座標（長さ単位はメートルがデフォルト）、角度 `ϕ ∈ [0,2π)` の角度単位（ラジアンがデフォルト）、高さ `z ∈ [0,∞)` の長さ単位（メートルがデフォルト）および指定された `Datum`（デフォルトは `NoDatum`）。

## 例

```julia
Cylindrical(1, π/4, 1) # デフォルト単位を追加
Cylindrical(1m, (π/4)rad, 1m) # 整数は浮動小数点数に変換される
Cylindrical(1.0m, 45°, 1.0m) # 度はラジアンに変換される
Cylindrical(1.0km, (π/4)rad, 1.0km)
Cylindrical{WGS84Latest}(1.0m, (π/4)rad, 1.0m)
```

## 参考文献

  * [円柱座標系](https://en.wikipedia.org/wiki/Cylindrical_coordinate_system)
  * [ISO 80000-2:2019](https://www.iso.org/standard/64973.html)
  * [ISO 80000-3:2019](https://www.iso.org/standard/64974.html)
