```
BoltzmannODE([; b_hint, d_dob_hint])
```

半無限問題を解くためのデフォルトアルゴリズム。

ボルツマン変換と（おそらく繰り返し）ODE統合を使用します。

# キーワード引数

  * `b_hint`: 境界値のためのオプションのヒント。
  * `d_dob_hint`: 境界 `o`-導関数のためのオプションのヒント。

# 参考文献

GERLERO, G. S.; BERLI, C. L. A.; KLER, P. A. Open-source high-performance software packages for direct and inverse solving of horizontal capillary flow. Capillarity, 2023, vol. 6, no. 2, p. 31-40.
