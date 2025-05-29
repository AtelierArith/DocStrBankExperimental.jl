```
𝒜(k::AbstractSPHKernel, r::T1,  h_inv::T1, Aⱼ::T2, mⱼ::T1, ρⱼ::T1 ) where {T1,T2}
```

Compute the contribution of particle `j` to the SPH quantity `A` for particle `i`. Based on Euclidean distance `r` between the particles.  Useful if many quantities need to be computed for the same particle pair.

$\vec{A}_i(x) ≈ \sum_j m_j \frac{\vec{A}_j}{\rho_j} W(r, h_i)$
