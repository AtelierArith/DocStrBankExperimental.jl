```
∇x𝒜(k::AbstractSPHKernel, h_inv::T1, xᵢ::T2, xⱼ::T2, Aⱼ::T2, mⱼ::T1, ρⱼ::T1 ) where {T1,T2}
```

Compute the contribution of particle `j` to the curl of the SPH quantity `A` for particle `i`.

$∇×\vec{A}_i(x) ≈ - \sum_j \frac{m_j}{\rho_j} \vec{A}_j \times ∇W(\vec{x}_i - \vec{x}_j, h_i)$
