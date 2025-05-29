```julia
mutable struct GaussianKineticEnergy{T<:(AbstractMatrix), S<:(AbstractMatrix)} <: BaytesMCMC.EuclideanKineticEnergy
```

Gaussian kinetic energy, which is independent of `q`.

# Fields

  * `Σ::AbstractMatrix`: Inverse Mass Matrix Σ ~ Posterior Covariance Matrix
  * `Mᶜʰᵒˡ::AbstractMatrix`: Cholesky decomposition of Mass matrix M, s.t. Mᶜʰᵒˡ*Mᶜʰᵒˡ'=M. Used to generate random draws
