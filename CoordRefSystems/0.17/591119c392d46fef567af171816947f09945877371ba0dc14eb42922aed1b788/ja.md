```
PlateCarree(x, y)
PlateCarree{Datum}(x, y)
```

Plate Carrée座標は、指定された`Datum`（デフォルトは`WGS84`）で長さ単位（デフォルトはメートル）です。

## 例

```julia
PlateCarree(1, 1) # デフォルトの単位を追加
PlateCarree(1m, 1m) # 整数は浮動小数点数に変換されます
PlateCarree(1.0km, 1.0km) # 長さの量はメートルに変換されます
PlateCarree(1.0m, 1.0m)
PlateCarree{WGS84Latest}(1.0m, 1.0m)
```

[EPSG:32662](https://epsg.io/32662)を参照してください。
