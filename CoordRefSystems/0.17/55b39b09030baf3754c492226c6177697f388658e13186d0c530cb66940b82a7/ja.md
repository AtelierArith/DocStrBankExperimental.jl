```
OrthoNorth(x, y)
OrthoNorth{Datum}(x, y)
```

与えられた `Datum`（デフォルトは `WGS84`）で、長さ単位（デフォルトはメートル）での正射北極座標。

## 例

```julia
OrthoNorth(1, 1) # デフォルト単位を追加
OrthoNorth(1m, 1m) # 整数は浮動小数点数に変換される
OrthoNorth(1.0km, 1.0km) # 長さの量はメートルに変換される
OrthoNorth(1.0m, 1.0m)
OrthoNorth{WGS84Latest}(1.0m, 1.0m)
```
