```
basin_entropy(basin; eps_x=20, eps_y=20)
```

このアルゴリズムは、規則的なグリッド上の計算された引力盆地の盆地エントロピーを計算します。関数は盆地エントロピーと境界盆地エントロピーを返します。

[A. Daza, A. Wagemakers, B. Georgeot, D. Guéry-Odelin and M. A. F. Sanjuán, Basin entropy: a new tool to analyze uncertainty in dynamical systems, Sci. Rep., 6, 31416, (2016).]

## 引数

  * `basin` : 盆地の情報を含む行列。

## キーワード引数

  * `eps_x`, `eps_y` : 盆地をサンプリングするために使用されるボックスのサイズを定義します。
