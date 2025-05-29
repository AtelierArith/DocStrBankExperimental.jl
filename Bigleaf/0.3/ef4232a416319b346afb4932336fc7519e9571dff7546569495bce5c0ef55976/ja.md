```
calc_sun_position_MOD(JD::Number)
```

ジュリア日 `JD` における太陽の位置を計算します。

結果は、平均日点の等式 (MOD) で表され、すなわち歳差を考慮しますが、摂動や極軸の小さな変動は考慮しません。球面黄道および赤道座標系で表現されます。このアルゴリズムは [Vallado 2013, p. 277-279] から適応されました。

# 引数:

  * `JD`: ジュリア日として与えられる時間。

# 値

`NamedTuple`: 太陽の位置

  * 黄道座標 (1:3)

      * λ: 太陽の黄道経度 [rad].
      * β: 太陽の黄道緯度 [rad] は 0 と仮定されます。
      * r: 地球から太陽までの距離 [m].
  * 赤道座標 (4:5)  

      * α: 昇交 [rad]
      * δ: 減交 [rad]
  * ϵ: 黄道傾斜 [rad].

# 参考文献

  * Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications.      Microcosm Press, Hawthorne, CA.
