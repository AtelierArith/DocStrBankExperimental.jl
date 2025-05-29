```
IntPoint(x, y)
```

整数値からIntPointを作成します。

```
IntPoint(x, y, magnitude, precision)
```

指定された桁数の精度で浮動小数点値からIntPointを作成します。 magnitude = ゼロ以上の桁数 (90 => 2, 9 => 1, 0.9 => 0, 0.09 => -1) sigdigits = 保存する桁数 (94.3856を4桁で => 94.39)

```julia
a = IntPoint(5.483, 55.8739, 2, 4) # [548, 5587]
b,c = tofloat(a, 2, 4)             # 5.48, 55.87
```
