```
WebMercator(x, y)
WebMercator{Datum}(x, y)
```

Web Mercator座標は、指定された`Datum`（デフォルトは`WGS84`）で長さ単位（デフォルトはメートル）です。

## 例

```julia
WebMercator(1, 1) # デフォルト単位を追加
WebMercator(1m, 1m) # 整数は浮動小数点数に変換されます
WebMercator(1.0km, 1.0km) # 長さの量はメートルに変換されます
WebMercator(1.0m, 1.0m)
WebMercator{WGS84Latest}(1.0m, 1.0m)
```

[EPSG:3857](https://epsg.io/3857)を参照してください。
