```
MatrixFactorization(
    data::DataAccessor,
    n_factors::Integer
)
```

行列因子分解（MF）に基づく推薦。因子の数 $k$ は `n_factors` で設定されます。

MFは、観測されたユーザー-アイテムの相互作用のセット $\mathcal{S} = \{(u, i) \in \mathcal{U} \times \mathcal{I}\}$ に対して、以下の最小化問題を解決します：

$$
\min_{P, Q} \sum_{(u, i) \in \mathcal{S}} \left( r_{u,i} - \mathbf{p}_u^{\mathrm{T}} \mathbf{q}_i \right)^2 + \lambda \ (\|\mathbf{p}_u\|^2 + \|\mathbf{q}_i\|^2),
$$

ここで、$\mathbf{p}_u, \mathbf{q}_i \in \mathbb{R}^k$ はそれぞれ因子化されたユーザーおよびアイテムベクトルであり、$\lambda$ は過学習を避けるための正則化パラメータです。最適な解は確率的勾配降下法（SGD）によって見つけられます。最終的に、$R$ の欠損値を予測するには、単に $PQ^{\mathrm{T}}$ を計算するだけで、予測は直接的に推薦につながります。
