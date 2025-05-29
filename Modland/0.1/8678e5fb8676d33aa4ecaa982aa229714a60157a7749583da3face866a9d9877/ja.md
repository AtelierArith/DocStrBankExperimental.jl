```
latlon_to_sinusoidal(lat::Float64, lon::Float64)::Tuple{Float64,Float64}
```

緯度と経度の座標を正弦投影座標に変換します。

# 引数

  * `lat::Float64`: 度単位の緯度。
  * `lon::Float64`: 度単位の経度。

# 戻り値

  * `Tuple{Float64, Float64}`: 正弦投影座標 (x, y)。
