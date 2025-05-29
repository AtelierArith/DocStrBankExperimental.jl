```
kernel_quantity(k::AbstractSPHKernel, h_inv::T1, 
                xᵢ::T2, xⱼ::T2, Aⱼ::T2, mⱼ::T1, ρⱼ::T1 ) where {T1,T2}
```

粒子 `j` が粒子 `i` の SPH 量 `A` に寄与する計算を行います。位置 `xᵢ` と `xⱼ` に基づいています。

$$
\vec{A}_i(x) ≈ \sum_j m_j \frac{\vec{A}_j}{\rho_j} W(\vec{x}_i - \vec{x}_j, h_i)
$$
