```
mag_to_absmag(mag::Level, redshift::Float64; H0::Unitful.Quantity{Float64}=70.0u"km/s/Mpc")
```

`mag`を絶対等級に変換します。`mag - 5 log10(c * redshift / (H0 * 10pc))`を計算します。

# 引数

  * `mag::Level`: 変換する等級
  * `redshift::Float64`: 赤方偏移、対象までの距離を計算するために使用されます
  * `;H0::Unitful.Quantity{Float64}=70.0u"km/s/Mpc`: 対象までの距離を計算するために使用されるH0の仮定値
