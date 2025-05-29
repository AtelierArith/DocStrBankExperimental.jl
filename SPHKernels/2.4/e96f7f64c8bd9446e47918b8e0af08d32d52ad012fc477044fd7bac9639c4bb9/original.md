```
kernel_quantity(k::AbstractSPHKernel, h_inv::T1, 
                xᵢ::T2, xⱼ::T2, Aⱼ::T2, mⱼ::T1, ρⱼ::T1 ) where {T1,T2}
```

Compute the contribution of particle `j` to the SPH quantity `A` for particle `i`. Based on positions `xᵢ` and `xⱼ`.

$\vec{A}_i(x) ≈ \sum_j m_j \frac{\vec{A}_j}{\rho_j} W(\vec{x}_i - \vec{x}_j, h_i)$
