```
Behrmann(x, y)
Behrmann{Datum}(x, y)
```

Behrmann座標は長さ単位（デフォルトはメートル）で、指定された`Datum`（デフォルトは`WGS84`）を使用します。

## 例

```julia
Behrmann(1, 1) # デフォルト単位を追加
Behrmann(1m, 1m) # 整数は浮動小数点数に変換されます
Behrmann(1.0km, 1.0km) # 長さの量はメートルに変換されます
Behrmann(1.0m, 1.0m)
Behrmann{WGS84Latest}(1.0m, 1.0m)
```

[ESRI:54017](https://epsg.io/54017)を参照してください。
