```
Cartesian(x₁, x₂, ..., xₙ)
Cartesian{Datum}(x₁, x₂, ..., xₙ)
Cartesian((x₁, x₂, ..., xₙ))
Cartesian{Datum}((x₁, x₂, ..., xₙ))
```

N次元のデカルト座標 `x₁, x₂, ..., xₙ` は、長さの単位（デフォルトはメートル）で、指定された `Datum`（デフォルトは `NoDatum`）を持ちます。最初の3つの座標には、それぞれ `x`、`y`、`z` のプロパティを使用してアクセスできます。

## 例

```julia
Cartesian(1, 1) # デフォルトの単位を追加
Cartesian(1m, 1m) # 整数は浮動小数点数に変換されます
Cartesian(1.0km, 1.0km, 1.0km)
Cartesian{WGS84Latest}(1.0m, 1.0m)
```

## 参考文献

  * [デカルト座標系](https://en.wikipedia.org/wiki/Cartesian_coordinate_system)
  * [ISO 80000-2:2019](https://www.iso.org/standard/64973.html)
  * [ISO 80000-3:2019](https://www.iso.org/standard/64974.html)
