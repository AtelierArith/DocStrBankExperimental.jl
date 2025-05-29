```
MEWMC(λ, value)
```

スムージング定数 `λ` と初期値 `value` を持つ指数加重移動共分散行列統計量。

新しい観測 `x \in \mathbb{R}^p` に基づく $C_t$ の更新メカニズムは次のように与えられます。

$$
Z_t = (1 - λ)Z_{t-1} + λ \cdot xx'
$$

,

そしてチャート値は次のように定義されます。

$$
C_t = \text{tr}(Z_t) - \log|Z_t| - p
$$

。

### 参考文献

Hawkins, D. M., & Maboudou-Tchao, E. M. (2008). Multivariate Exponentially Weighted Moving Covariance Matrix. Technometrics, 50(2), 155-166.
