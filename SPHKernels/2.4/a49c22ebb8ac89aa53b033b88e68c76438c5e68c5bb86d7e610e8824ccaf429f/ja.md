```
𝒜(k::AbstractSPHKernel, h_inv::T1, 
  xᵢ::Union{T1, T2}, xⱼ::Union{T1, T2},
  Aⱼ::Union{T1, T2}, mⱼ::T1, ρⱼ::T1 ) where {T1,T2}
```

粒子 `j` の SPH 量 `A` が粒子 `i` に与える寄与を計算します。位置 `xᵢ` と `xⱼ` に基づいています。

$$
\vec{A}_i(x) ≈ \sum_j m_j \frac{\vec{A}_j}{\rho_j} W(\vec{x}_i - \vec{x}_j, h_i)
$$
