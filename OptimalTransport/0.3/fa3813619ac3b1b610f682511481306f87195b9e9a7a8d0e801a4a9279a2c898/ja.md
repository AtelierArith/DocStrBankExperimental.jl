```
sinkhorn_barycenter(μ, C, ε, w, alg = SinkhornGibbs(); kwargs...)
```

コレクションの `N` 個のヒストグラムが `μ` の列に含まれている場合のSinkhornバリセンターを計算します。コスト行列 `C` のサイズは `(size(μ, 1), size(μ, 1))` で、相対重み `w` のサイズは `N`、エントロピー正則化パラメータは `ε` です。`μ` のエントロピー正則化されたバリセンター、すなわち長さ `size(μ, 1)` のヒストグラム `ρ` を返します。これは次の式を解きます。

$$
\min_{\rho \in \Sigma} \sum_{i = 1}^N w_i \operatorname{OT}_{\varepsilon}(\mu_i, \rho)
$$

ここで、$\operatorname{OT}_{ε}(\mu, \nu) = \inf_{\gamma \Pi(\mu, \nu)} \langle \gamma, C \rangle + \varepsilon \Omega(\gamma)$ はコスト $C$ と正則化 $\epsilon$ を持つエントロピー最適輸送損失です。
