```
Sinusoidal(x, y)
Sinusoidal{Datum}(x, y)
```

サイン波 (サンソン-フラムスティード) 座標は、与えられた `Datum` (デフォルトは `WGS84`) に基づく長さ単位 (デフォルトはメートル) です。

## 例

```julia
Sinusoidal(1, 1) # デフォルトの単位を追加
Sinusoidal(1m, 1m) # 整数は浮動小数点数に変換されます
Sinusoidal(1.0km, 1.0km) # 長さの量はメートルに変換されます
Sinusoidal(1.0m, 1.0m)
Sinusoidal{WGS84Latest}(1.0m, 1.0m)
```

[サイン波投影](https://en.wikipedia.org/wiki/Sinusoidal_projection)を参照してください。
