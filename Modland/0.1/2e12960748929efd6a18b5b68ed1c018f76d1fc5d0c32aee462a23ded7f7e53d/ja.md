```
sinusoidal_to_modland(x::Float64, y::Float64)::String
```

正弦投影座標をMODIS土地タイルインデックスに変換します。

# 引数

  * `x::Float64`: 正弦 x 座標。
  * `y::Float64`: 正弦 y 座標。

# 戻り値

  * `String`: "hXXvYY" 形式のMODIS土地タイルインデックス。
