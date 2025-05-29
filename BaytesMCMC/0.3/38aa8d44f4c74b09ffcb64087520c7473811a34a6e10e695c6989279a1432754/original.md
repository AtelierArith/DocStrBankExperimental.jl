```julia
mutable struct Proposal{A<:BaytesCore.UpdateBool, T<:AbstractFloat, P<:(AbstractMatrix), C<:(AbstractMatrix), M<:BaytesMCMC.MatrixTune}
```

Proposal distribution container.

# Fields

  * `adaption::BaytesCore.UpdateBool`: Check if adaption true in current iteration
  * `chain::Matrix{T} where T<:AbstractFloat`: θᵤ samples in current MCMC Phase, used for Σ estimation
  * `Σ::AbstractMatrix`: Posterior Covariance estimate
  * `Σ⁻¹ᶜʰᵒˡ::AbstractMatrix`: Cholesky decomposition of Inverse Posterior Covariance matrix Σ, s.t. Σ⁻¹ᶜʰᵒˡ*Σ⁻¹ᶜʰᵒˡ'=Σ⁻¹. Used to generate random draws in HMC/NUTS sampler.
  * `matrixtune::BaytesMCMC.MatrixTune`: Tuning parameter for Σ estimation
