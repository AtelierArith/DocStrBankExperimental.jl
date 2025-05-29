```
OrthoSouth(x, y)
OrthoSouth{Datum}(x, y)
```

長さ単位（デフォルトはメートル）での正射影南極座標と指定された`Datum`（デフォルトは`WGS84`）。

## 例

```julia
OrthoSouth(1, 1) # デフォルト単位を追加
OrthoSouth(1m, 1m) # 整数は浮動小数点数に変換される
OrthoSouth(1.0km, 1.0km) # 長さの量はメートルに変換される
OrthoSouth(1.0m, 1.0m)
OrthoSouth{WGS84Latest}(1.0m, 1.0m)
```
