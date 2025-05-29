```
cio_iau2006(jd_tt::Number) -> Float64, Float64, Float64
```

天体中間極（CIP）の座標 `X` と `Y` を地心天体基準フレーム（GCRF）に対して計算し、CIOロケーター `s` を求めます。このアルゴリズムはIAU-2006理論に基づいています。

CIOロケーター `s` は、CIPがGCRSに対して動いているときの非回転原点の運動学的定義に対応するCIPの赤道上のCIOの位置を提供します。これは基準時刻と歳差および nutation による時刻の間のものです **[1]**(p. 214)。

# 戻り値

  * `Float64`: GCRFに対するCIPの座標 `X`。
  * `Float64`: GCRFに対するCIPの座標 `Y`。
  * `Float64`: CIOロケーター `s`。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications.  Microcosm   Press, Hawthorn, CA, USA.

```
