```
ot_plan(c, μ::ContinuousUnivariateDistribution, ν::UnivariateDistribution)
```

一様分布 `μ` と `ν` をソースおよびターゲットの周辺分布とし、コスト関数 `c` が $c(x, y) = h(|x - y|)$ の形であるモンジュ＝カントロビッチ問題の最適輸送計画を計算します。ここで、$h$ は凸関数です。

この設定において、最適輸送計画はモンジュ写像です。

$$
T = F_\nu^{-1} \circ F_\mu
$$

ここで、$F_\mu$ は `μ` の累積分布関数であり、$F_\nu^{-1}$ は `ν` の分位関数です。

参照: [`ot_cost`](@ref), [`emd`](@ref)
