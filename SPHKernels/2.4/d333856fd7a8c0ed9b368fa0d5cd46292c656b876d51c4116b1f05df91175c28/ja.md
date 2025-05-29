```
quantity_gradient(k::AbstractSPHKernel, h_inv::T1, 
                  xᵢ::T2, xⱼ::T2, Aⱼ::T2,
                  mⱼ::T1, ρⱼ::T1 ) where {T1<:Real, T2}

粒子 `j` の SPH 量 `A` の勾配への寄与を粒子 `i` に対して計算します。位置 `xᵢ` と `xⱼ` に基づいています。

$∇\vec{A}_i(x) ≈ \sum_j \frac{m_j}{\rho_j} \vec{A}_j \: ∇W(||\vec{x}_i - \vec{x}_j||, h_i)$
```
