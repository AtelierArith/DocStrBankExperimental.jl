```
relative_risk_contribution(weights, covariance_matrix)
```

# 数式

資産 `i` の相対リスク寄与度（`RRC`）は、資産のリスク寄与度 `RC_i` をポートフォリオ全体のリスク $\sigma(w)$ で割った比率として定義されます：

$$
\text{RRC}_i = \frac{\text{RC}_i}{\sigma(w)} = \frac{w_i(\Sigma w)_i}{w^T\Sigma w}
$$

したがって、$\sum_{i=1}^N \text{RRC}_i = 1$ です。

# 引数

  * `weights`:                ポートフォリオ内の資産の重みのベクトル。
  * `covariance_matrix`:      資産リターンの共分散行列。
