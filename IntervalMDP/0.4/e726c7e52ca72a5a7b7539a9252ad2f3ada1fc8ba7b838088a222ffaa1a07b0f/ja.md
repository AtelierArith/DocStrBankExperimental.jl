```
FiniteTimeReward{R <: Real, AR <: AbstractArray{R}, T <: Integer}
```

`FiniteTimeReward`は、各状態に各反復で割り当てられる報酬 $R : S \to \mathbb{R}$ の特性であり、割引率 $\gamma$ を持ちます。時間のホライズン $H$ は有限であるため、割引率はオプションであり、最適な方針は時間変化します。戦略 $\pi : S \to A$ が与えられたとき、この特性は次のようになります。

$$
    V(s_0) = \mathbb{E}\left[\sum_{k=0}^{H} \gamma^k R(s_k) \mid s_0, \pi\right].
$$
