```
fog_attenuation_db_per_km( frequency_ghz::Real, M, T_deg::Real )::Real
```

5 GHz以上の周波数に対する雨の減衰の経験的モデル。一方向の減衰はdB/kmで表されます。

# 引数

  * `frequency_ghz`	伝播する波の周波数。
  * `M`				水分濃度（g/m³）。
  * `T_deg`			気温（摂氏度）。

## 例

```jldoctest
julia> res = fog_attenuation_db_per_km( 10, 0.8, 23 );

julia> round(res, digits=6)
4.68976
```

## 参考文献

  * M. A. Richards と J. A. Scheer と W. A. Holm, Principles of Modern Radar, SciTech Publishing, 2010.
