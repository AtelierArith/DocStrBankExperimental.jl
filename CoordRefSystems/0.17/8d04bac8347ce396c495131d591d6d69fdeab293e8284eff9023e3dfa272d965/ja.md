```
EqualEarth(x, y)
EqualEarth{Datum}(x, y)
```

与えられた `Datum`（デフォルトは `WGS84`）を使用して、長さ単位（デフォルトはメートル）でのEqual Earth座標。

## 例

```julia
EqualEarth(1, 1) # デフォルト単位を追加
EqualEarth(1m, 1m) # 整数は浮動小数点数に変換される
EqualEarth(1.0km, 1.0km) # 長さの量はメートルに変換される
EqualEarth(1.0m, 1.0m)
EqualEarth{WGS84Latest}(1.0m, 1.0m)
```

[Equal Earth projection](https://equal-earth.com/equal-earth-projection.html)を参照してください。
