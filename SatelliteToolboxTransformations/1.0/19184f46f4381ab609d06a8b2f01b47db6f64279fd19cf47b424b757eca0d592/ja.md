```
nutation_fk5(jd_tt::Number, n_max::Number = 106, nut_coefs_1980::Matrix = _IAU_1980_NUTATION_COEFFICIENTS)
```

ジュリア日 `jd_tt` [地球時間] における摂動パラメータを1980年IAU摂動理論を用いて計算します。係数は `nut_coefs_1980` で、各行は以下の構文を持つ行列でなければなりません **[1]**(p.  1043):

```
an1  an2  an3  an4  an5  Ai  Bi  Ci  Di
```

ここで、`Ai` と `Ci` の単位は [0.0001"] で、`Bi` と `Di` の単位は [0.0001"/JC] です。ユーザーは、摂動を計算する際に使用される係数の数 `n_max` を指定することもできます。`n_max` が省略された場合、デフォルトは106になります。

# 戻り値

  * `Float64`: 黄道の平均傾斜 [rad].
  * `Float64`: 黄道の傾斜における摂動 [rad].
  * `Float64`: 経度における摂動 [rad].

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.

```
