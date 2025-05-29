```
ot_plan(::SqEuclidean, μ::MvNormal, ν::MvNormal)
```

多変量正規分布 `μ` と `ν` をソースおよびターゲットの周辺分布とし、コスト関数 $c(x, y) = \|x - y\|_2^2$ を用いてモンジュ＝カントロビッチ問題の最適輸送計画を計算します。

この設定において、$\mu = \mathcal{N}(m_\mu, \Sigma_\mu)$ および $\nu = \mathcal{N}(m_\nu, \Sigma_\nu)$ の場合、最適輸送計画はモンジュ写像です。

$$
T \colon x \mapsto m_\nu
+ \Sigma_\mu^{-1/2}
{\big(\Sigma_\mu^{1/2} \Sigma_\nu \Sigma_\mu^{1/2}\big)}^{1/2}\Sigma_\mu^{-1/2}
(x - m_\mu).
$$

参照: [`ot_cost`](@ref), [`emd`](@ref)
