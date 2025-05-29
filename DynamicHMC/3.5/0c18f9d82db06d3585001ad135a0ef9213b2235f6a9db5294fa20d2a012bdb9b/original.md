```julia
struct GaussianKineticEnergy{T<:(AbstractMatrix), S<:(AbstractMatrix)} <: DynamicHMC.EuclideanKineticEnergy
```

Gaussian kinetic energy, with $K(q,p) = p ∣ q ∼ 1/2 pᵀ⋅M⁻¹⋅p + log|M|$ (without constant), which is independent of $q$.

The inverse covariance $M⁻¹$ is stored.

!!! note
    Making $M⁻¹$ approximate the posterior variance is a reasonable starting point.

