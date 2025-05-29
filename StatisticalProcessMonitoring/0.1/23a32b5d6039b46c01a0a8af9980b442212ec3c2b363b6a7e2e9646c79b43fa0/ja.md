```
MEWMS(λ, value)
```

スムージング定数 `λ` を持つ指数加重移動共分散行列。

新しい観測値 `x \in \mathbb{R}^p` に基づく更新メカニズムは次のように与えられます。

$$
Z_t = (1 - λ)\cdot Z_{t-1} + λ \cdot xx'
$$

、

チャート値は次のように定義されます。

$$
C_t = \textrm{tr}(Z_t).
$$

### 参考文献

Huwang, L., Yeh, A. B., & Wu, C.-W. (2007). Monitoring Multivariate Process Variability for Individual Observations. Journal of Quality Technology, 39(3), 258-278. https://doi.org/10.1080/00224065.2007.11917692
