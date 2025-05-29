```
WinkelTripel(x, y)
WinkelTripel{Datum}(x, y)
```

Winkel Tripel座標は、指定された`Datum`（デフォルトは`WGS84`）で長さ単位（デフォルトはメートル）です。

## 例

```julia
WinkelTripel(1, 1) # デフォルト単位を追加
WinkelTripel(1m, 1m) # 整数は浮動小数点数に変換されます
WinkelTripel(1.0km, 1.0km) # 長さの量はメートルに変換されます
WinkelTripel(1.0m, 1.0m)
WinkelTripel{WGS84Latest}(1.0m, 1.0m)
```

[ESRI:54042](https://epsg.io/54042)を参照してください。
