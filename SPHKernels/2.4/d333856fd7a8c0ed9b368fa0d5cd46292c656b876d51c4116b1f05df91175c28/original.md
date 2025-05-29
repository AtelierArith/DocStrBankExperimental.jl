```
quantity_gradient(k::AbstractSPHKernel, h_inv::T1, 
                  xᵢ::T2, xⱼ::T2, Aⱼ::T2,
                  mⱼ::T1, ρⱼ::T1 ) where {T1<:Real, T2}
```

Compute the contribution of particle `j` to the gradient of the SPH quantity `A` for particle `i`. Based on positions `xᵢ` and `xⱼ`.

$∇\vec{A}_i(x) ≈ \sum_j \frac{m_j}{\rho_j} \vec{A}_j \: ∇W(||\vec{x}_i - \vec{x}_j||, h_i)$
