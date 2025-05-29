```
DiagonalPSB(d)
```

対角PSB準ニュートン近似を表す線形演算子を構築します。これは以下に記載されています。

M. Zhu, J. L. Nazareth and H. Wolkowicz The Quasi-Cauchy Relation and Diagonal Updating. SIAM Journal on Optimization, vol. 9, number 4, pp. 1192-1204, 1999. https://doi.org/10.1137/S1052623498331793.

この近似は弱接線方程式を満たし、正定値であることは保証されていません。

# 引数

  * `d::AbstractVector`: 初期対角近似。
