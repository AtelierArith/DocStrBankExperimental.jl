```
ot_cost(::SqEuclidean, μ::MvNormal, ν::MvNormal)
```

正規分布 `μ` と `ν` の間の二乗2-ワッサースタイン距離を、ソースおよびターゲットの周辺分布として計算します。

この設定では、最適輸送コストは次のように計算できます。

$$
W_2^2(\mu, \nu) = \|m_\mu - m_\nu \|^2 + \mathcal{B}(\Sigma_\mu, \Sigma_\nu)^2,
$$

ここで、$\mu = \mathcal{N}(m_\mu, \Sigma_\mu)$、$\nu = \mathcal{N}(m_\nu, \Sigma_\nu)$、および $\mathcal{B}$ はブーレス距離です。

参照: [`ot_plan`](@ref), [`emd2`](@ref)
