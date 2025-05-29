```
Robinson(x, y)
Robinson{Datum}(x, y)
```

ロビンソン座標は、指定された`Datum`（デフォルトは`WGS84`）で長さ単位（デフォルトはメートル）です。

## 例

```julia
Robinson(1, 1) # デフォルト単位を追加
Robinson(1m, 1m) # 整数は浮動小数点数に変換されます
Robinson(1.0km, 1.0km) # 長さの量はメートルに変換されます
Robinson(1.0m, 1.0m)
Robinson{WGS84Latest}(1.0m, 1.0m)
```

[ESRI:54030](https://epsg.io/54030)を参照してください。
