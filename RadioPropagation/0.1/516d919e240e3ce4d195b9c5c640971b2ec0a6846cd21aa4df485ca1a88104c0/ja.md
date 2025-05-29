```
rain_attenuation_db_per_km_circular_pol( frequency_ghz::Real, fall_rate_mm_hour::Real )::Real
```

1から400 GHzの周波数に対する雨の減衰の経験的モデル、円偏光。モデルは基礎データの最も近い周波数を使用します。片道の減衰はdB/kmで表されます。

# 引数

  * `frequency_ghz`     	伝播する波の周波数。
  * `fall_rate_mm_hour`	雨の強度 [mm/h]。

## 例

```jldoctest
julia> res = rain_attenuation_db_per_km_circular_pol( 30, 20 );

julia> round(res, digits=6)
3.675503
```

## 参考文献

  * M. A. Richards と J. A. Scheer と W. A. Holm, Principles of Modern Radar, SciTech Publishing, 2010.
