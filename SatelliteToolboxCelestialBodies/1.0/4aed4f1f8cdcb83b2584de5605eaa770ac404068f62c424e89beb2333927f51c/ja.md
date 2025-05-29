```
sun_velocity_mod(jd_tdb::Number) -> SVector{3, Float64}
sun_velocity_mod(date_tdb::DateTime) -> SVector{3, Float64}
```

ジュリア日 `jd_tdb` または `date_tdb` において、IAU-76/FK5 MOD（平均赤道、日付の平均春分点）で測定され、表現された太陽の速度を計算します。入力時間は重心動力学時間（TDB）で表現されなければなりません。このアルゴリズムは、[1, p. 277-279] における太陽位置の時間微分を計算することによって得られました。

!!! note
    この関数は、必要な精度のために `Float64` を使用してすべての計算を行います。


# References

  * **[1]** Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. 4th ed.   Microcosm Press, Hawthorne, CA.
