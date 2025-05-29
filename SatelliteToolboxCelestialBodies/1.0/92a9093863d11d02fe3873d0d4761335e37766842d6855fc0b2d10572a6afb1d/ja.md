```
sun_position_mod(jd_tdb::Number) -> SVector{3, Float64}
sun_position_mod(date_tdb::DateTime) -> SVector{3, Float64}
```

ジュリアンデイ `jd_tdb` または `date_tdb` におけるIAU-76/FK5 MOD（平均赤道、日付の平均春分点）で表される太陽の位置を計算します。入力時間は重心動力学時間（TDB）で表される必要があります。このアルゴリズムは [1, pp. 277-279] から適応されました。

!!! 注意     この関数は必要な精度のために `Float64` を使用してすべての計算を行います。

# 参考文献

  * **[1]** Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. 4th ed.   Microcosm Press, Hawthorne, CA.
