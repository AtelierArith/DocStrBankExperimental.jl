```
moon_position_mod(jd_tdb::Number[, model]) -> SVector{3, Float64}
moon_position_mod(date_tdb::DateTime[, model]) -> SVector{3, Float64}
```

ジュリアンデイ `jd_tdb` または `date_tdb` におけるIAU-76/FK5 MOD（平均赤道、日付の平均春分点）で表される月の位置を計算します。入力時間は重心動力学時間（TDB）で表される必要があります。

`model` は `Val(:Meeus)` または `Val(:Vallado)` でなければなりません。 `Val(:Meeus)` は **[2, p. 337]** にあるアルゴリズムを使用しており、経度で10"、緯度で4"の精度を提供します（参考文献では期間については言及されていません）。 `Val(:Vallado)` は **[1, p. 288]** にあるアルゴリズムを使用しており、`Val(:Meeus)` よりも10倍速いですが、経度で0.3°、緯度で0.2°の誤差を引き起こす可能性があります。

!!! note
    この関数は必要な精度のために `Float64` を使用してすべての計算を行います。


# 参考文献

  * **[1]** Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. 4th ed.   Microcosm Press, Hawthorne, CA.
  * **[2]** Meeus, J (1998). Astronomical algorithms. Willmann-Bell, Inc, Richmond, VA.
