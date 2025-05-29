```
∇dot𝒜(k::AbstractSPHKernel, h_inv::T1, xᵢ::T2, xⱼ::T2, Aⱼ::T2, mⱼ::T1, ρⱼ::T1 ) where {T1,T2}

粒子 `j` の SPH 量 `A` の発散に対する寄与を粒子 `i` のために計算します。 [`quantity_divergence`](@ref) のコンパクトな表記。

$∇\cdot\vec{A}_i(x) ≈ \sum_j \frac{m_j}{\rho_j} \vec{A}_j \cdot ∇W(\vec{x}_i - \vec{x}_j, h_i)$
```
