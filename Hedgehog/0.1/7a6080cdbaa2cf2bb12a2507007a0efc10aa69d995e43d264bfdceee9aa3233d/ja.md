```
Interpolator2D{T, S, U, F}
```

2D 補間構造体で、以下の要素を含みます：

  * `x_vals`: x方向のグリッド（例：満期）、
  * `y_vals`: y方向のグリッド（例：行使価格）、
  * `y_interps`: y方向の補間器、xごとに1つ、
  * `build_x_interp`: すべてのy補間器を`y`で適用して構築された関数 `y ↦ x-interpolator`。
