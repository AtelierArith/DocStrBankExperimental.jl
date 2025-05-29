```
add_noise!(
    # ARGUMENTS
    Cτ_noisy::AbstractVector{T};
    # KEYWORD ARGUMENTS
    Cτ_exact::AbstractVector{T},
    τ::AbstractVector{T},
    σ::T,
    ξ::T,
    sum_rule::Function = C0 -> 1 - C0,
    noise_type::Symbol = :TruncatedNormal
) where {T<:AbstractFloat}

add_noise!(
    # ARGUMENTS
    Cτ_noisy::AbstractMatrix{T};
    # KEYWORD ARGUMENTS
    Cτ_exact::AbstractVector{T},
    τ::AbstractVector{T},
    σ::T,
    ξ::T,
    sum_rule::Function = C0 -> 1 - C0,
    noise_type::Symbol = :TruncatedNormal
) where {T<:AbstractFloat}
```

Add noise to an imaginary time correlation function $C(\tau)$ that is exponentially correlated in imaginary time. See [`add_noise`](@ref) for more information.

## Arguments

  * `Cτ_noisy`: The array to which the noisy $C(\tau)$ data will be written. If a matrix and not a vector then the columns correspond to samples and the rows to the imaginary time slices $\tau$.

## Keyword Arguments

  * `Cτ_exact::AbstractVector{T}`: Vector containing the exact values for $C(\tau)$.
  * `τ::AbstractVector{T}`: Vector specifying the imaginary time $\tau$ grid that $C(\tau)$ is evaluated on. Assumes that the last element equals the inverse temperature, i.e. `τ[end] = β`.
  * `σ::T`: Standard deviation of the noise; controls the typical amplitude of the error.
  * `ξ::T`: Correlation length associated with the noise in imaginary time.
  * `sum_rule::Function = C0 -> 1 - C0`: Enforces sum rule, or bounday condition in imaginay time. Default behavior assumes a fermionic correlation function, enforcing that $C(\beta) = 1 - C(0)$.
  * `noise_type::Symbol = :TruncatedNormal`: Distribution that the noise is sampled from prior to correlations being introduced in imaginary time. Available options are `noise_type ∈ (:TruncatedNormal, :Gamma, :Normal)`.
