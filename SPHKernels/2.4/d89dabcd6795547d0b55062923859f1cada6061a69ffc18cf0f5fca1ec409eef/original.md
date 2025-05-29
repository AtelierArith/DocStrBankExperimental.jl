```
∇𝒜( k::AbstractSPHKernel, h_inv, xᵢ, xⱼ, Aⱼ, mⱼ, ρⱼ)
```

Compute the contribution of particle `j` to the gradient of the SPH quantity `A` for particle `i`. Compact notation of [`quantity_gradient`](@ref).

$∇\vec{A}_i(x) ≈ \sum_j \frac{m_j}{\rho_j} \vec{A}_j \: ∇W(||\vec{x}_i - \vec{x}_j||, h_i)$
