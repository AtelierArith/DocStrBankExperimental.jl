```
indicator(y, b; indregion=:above, ineq=:nonstrict)
```

デフォルト形式の指標変数 $\mathbf{1}\{y ≥ b\}$。不等式は厳密にすることができ、不等式の向きを反転させることができます。

# 引数

  * `ineq=:nonstrict` (デフォルト): $\mathbf{1}\{y ≥ b\}$ または

$$
\mathbf{1}\{y ≤ b\}
$$

を計算します。

  * `ineq=:strict`: $\mathbf{1}\{y > b\}$ または $\mathbf{1}\{y < b\}$ を計算します。
  * `indregion=:above` (デフォルト): $\mathbf{1}\{y ≥ b\}$ または

$$
\mathbf{1}\{y > b\}
$$

を計算します。

  * `indregion=:below`: $\mathbf{1}\{y ≤ b\}$ または $\mathbf{1}\{y < b\}$ を計算します。
