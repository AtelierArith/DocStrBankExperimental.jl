```
rain_attenuation_db_per_km( polarization::Symbol, frequency_ghz::Real, fall_rate_mm_hour::Real )::Real
```

1から400 GHzの周波数のRF雨減衰の経験的モデル、線形偏波。モデルは基礎データの最も近い周波数を使用します。

# 引数

  * `polarization`        偏波、`:vertical`、`:horizontal`。
  * `frequency_ghz`     	伝播波の周波数。
  * `fall_rate_mm_hour`	雨の強度 [mm/h]。

## 例

```jldoctest
julia> res = rain_attenuation_db_per_km( :vertical , 30, 20 );

julia> round(res, digits=6)
3.34
```

## 参考文献

  * M. A. Richards と J. A. Scheer と W. A. Holm, Principles of Modern Radar, SciTech Publishing, 2010.
