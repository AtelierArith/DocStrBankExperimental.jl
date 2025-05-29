```
𝒜(k::AbstractSPHKernel, r::T1,  h_inv::T1, Aⱼ::T2, mⱼ::T1, ρⱼ::T1 ) where {T1,T2}
```

粒子 `j` が粒子 `i` のために SPH 量 `A` に寄与する計算を行います。粒子間のユークリッド距離 `r` に基づいています。同じ粒子ペアに対して多くの量を計算する必要がある場合に便利です。

$$
\vec{A}_i(x) ≈ \sum_j m_j \frac{\vec{A}_j}{\rho_j} W(r, h_i)
$$
