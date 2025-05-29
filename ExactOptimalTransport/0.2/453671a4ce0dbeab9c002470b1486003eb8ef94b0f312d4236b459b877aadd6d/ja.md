```
ot_cost(
    c, μ::ContinuousUnivariateDistribution, ν::UnivariateDistribution; plan=nothing
)
```

一様分布 `μ` と `ν` をソースおよびターゲットの周辺分布とし、コスト関数 `c` が $c(x, y) = h(|x - y|)$ の形を持つモンジュ＝カントロビッチ問題の最適輸送コストを計算します。ここで、$h$ は凸関数です。

この設定では、最適輸送コストは次のように計算できます。

$$
\int_0^1 c(F_\mu^{-1}(x), F_\nu^{-1}(x)) \mathrm{d}x
$$

ここで、$F_\mu^{-1}$ と $F_\nu^{-1}$ はそれぞれ `μ` と `ν` の分位関数です。

事前に計算された最適輸送 `plan` を提供することができます。

参照: [`ot_plan`](@ref), [`emd2`](@ref)
