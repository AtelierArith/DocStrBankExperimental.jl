```
quantity_gradient(k::AbstractSPHKernel,
                  r::T1, h_inv::T1,
                  Δx::T2, Aⱼ::T2,
                  mⱼ::T1, ρⱼ::T1) where {T1<:Real,T2}

粒子 `j` の SPH 量 `A` の勾配への寄与を粒子 `i` のために計算します。粒子間のユークリッド距離 `r` と距離ベクトル `Δx` に基づいています。同じ粒子ペアに対して多くの量を計算する必要がある場合に便利です。

$∇\vec{A}_i(x) ≈ \sum_j \frac{m_j}{\rho_j} \vec{A}_j \: ∇W(||\vec{x}_i - \vec{x}_j||, h_i)$
```
