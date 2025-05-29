```
atmospheric_attenuation_db_per_km( frequency_ghz::Real, T_kelvin::Real=288.15, water_vapour_density_g_m³::Real=7.5, dry_air_pressure_h_pa::Real=1013.25 )::Real
```

周波数が1 - 1000 GHzの範囲における大気中の気体による減衰の経験的モデル。一方向の減衰をdB/kmで示します。

# 引数

  * `frequency_ghz`				伝播する波の周波数。
  * `T_kelvin`					ケルビンでの絶対温度。
  * `water_vapour_density_g_m³` 	g/m³での水蒸気密度。
  * `dry_air_pressure_h_pa`		hPaでの乾燥空気圧。

## 例

```jldoctest
julia> res = atmospheric_attenuation_db_per_km( 22 );

julia> round(res, digits=6)
0.187337
```

## 参考文献

  * Rec. ITU-R P.676-12, 大気中の気体による減衰と関連する影響, ITU-R 2020.
