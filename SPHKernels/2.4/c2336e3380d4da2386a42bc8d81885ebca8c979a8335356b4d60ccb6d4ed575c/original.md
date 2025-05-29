```
quantity_gradient(k::AbstractSPHKernel,
                  r::T1, h_inv::T1,
                  Δx::T2, Aⱼ::T2,
                  mⱼ::T1, ρⱼ::T1) where {T1<:Real,T2}
```

Compute the contribution of particle `j` to the gradient of the SPH quantity `A` for particle `i`. Based on Euclidean distance `r` and distance vector `Δx` between the particles.  Useful if many quantities need to be computed for the same particle pair.

$∇\vec{A}_i(x) ≈ \sum_j \frac{m_j}{\rho_j} \vec{A}_j \: ∇W(||\vec{x}_i - \vec{x}_j||, h_i)$
