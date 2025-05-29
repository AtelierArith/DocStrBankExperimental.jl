```
GallPeters(x, y)
GallPeters{Datum}(x, y)
```

Gall-Peters座標は長さ単位（デフォルトはメートル）で、指定された`Datum`（デフォルトは`WGS84`）を使用します。

## 例

```julia
GallPeters(1, 1) # デフォルト単位を追加
GallPeters(1m, 1m) # 整数は浮動小数点数に変換されます
GallPeters(1.0km, 1.0km) # 長さの量はメートルに変換されます
GallPeters(1.0m, 1.0m)
GallPeters{WGS84Latest}(1.0m, 1.0m)
```
