```
Lambert(x, y)
Lambert{Datum}(x, y)
```

長さ単位（デフォルトはメートル）でのランバート円筒等面積座標と指定された`Datum`（デフォルトは`WGS84`）。

## 例

```julia
Lambert(1, 1) # デフォルト単位を追加
Lambert(1m, 1m) # 整数は浮動小数点数に変換される
Lambert(1.0km, 1.0km) # 長さの量はメートルに変換される
Lambert(1.0m, 1.0m)
Lambert{WGS84Latest}(1.0m, 1.0m)
```

[ESRI:54034](https://epsg.io/54034)を参照してください。
