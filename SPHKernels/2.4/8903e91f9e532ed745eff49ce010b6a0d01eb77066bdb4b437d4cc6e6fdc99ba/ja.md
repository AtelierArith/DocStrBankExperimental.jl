```
quantity_curl(k::AbstractSPHKernel, h_inv::T1, xᵢ::T2, xⱼ::T2, Aⱼ::T2, mⱼ::T1, ρⱼ::T1 ) where {T1,T2}
```

粒子 `j` の SPH 量 `A` が粒子 `i` のカールに寄与する計算を行います。

$$
∇×\vec{A}_i(x) ≈ - \sum_j \frac{m_j}{\rho_j} \vec{A}_j \times ∇W(\vec{x}_i - \vec{x}_j, h_i)
$$
