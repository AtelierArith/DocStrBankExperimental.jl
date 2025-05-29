```
precession_fk5(jd_tt::Number) -> (Float64, Float64, Float64)
```

ジュリア日 `jd_tt` [地球時間] における歳差運動に関連する角度をIAU-76/FK5理論を使用して計算します。

# 戻り値

  * `NTuple{3, Float64}`: **[1]**(p. 226-228) に記載されている角度 (ζ, Θ, z)。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.
