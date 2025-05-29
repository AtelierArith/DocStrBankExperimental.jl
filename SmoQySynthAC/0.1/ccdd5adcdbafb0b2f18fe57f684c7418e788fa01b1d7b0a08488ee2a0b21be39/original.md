```
add_noise(;
    # KEYWORD ARGUMENTS
    Cτ_exact::AbstractVector{T},
    τ::AbstractVector{T},
    σ::T,
    ξ::T,
    sum_rule::Function = C0 -> 1 - C0,
    noise_type::Symbol = :TruncatedNormal
) where {T<:AbstractFloat}

add_noise(
    # ARGUMENTS
    N_samples::Int;
    # KEYWORD ARGUMENTS
    Cτ_exact::AbstractVector{T},
    τ::AbstractVector{T},
    σ::T,
    ξ::T,
    sum_rule::Function = C0 -> 1 - C0,
    noise_type::Symbol = :TruncatedNormal
) where {T<:AbstractFloat}
```

Add noise to an imaginary time correlation function $C(\tau)$ that is exponentially correlated in imaginary time.

## Arguments

  * `N_samples` (optional): Number of random samples to generate. If passed this function returns a matrix where the columsn correspond to the different samples.

## Keyword Arguments

  * `Cτ_exact::AbstractVector{T}`: Vector containing the exact values for $C(\tau)$.
  * `τ::AbstractVector{T}`: Vector specifying the imaginary time $\tau$ grid that $C(\tau)$ is evaluated on. Assumes that the last element equals the inverse temperature, i.e. `τ[end] = β`.
  * `σ::T`: Standard deviation of the noise; controls the typical amplitude of the error.
  * `ξ::T`: Correlation length associated with the noise in imaginary time.
  * `sum_rule::Function = C0 -> 1 - C0`: Enforces sum rule, or bounday condition in imaginay time. Default behavior assumes a fermionic correlation function, enforcing that $C(\beta) = 1 - C(0)$.
  * `noise_type::Symbol = :TruncatedNormal`: Distribution that the noise is sampled from prior to correlations being introduced in imaginary time. Available options are `noise_type ∈ (:TruncatedNormal, :Gamma, :Normal)`.

## Additional Information

If the correlation function $C(\tau_i)$ the corresponding noisy correlation function is given by

$$
C_{\rm noisy}(\tau_i) = C(\tau_i) + \frac{\sum_j e^{-|\tau_j-\tau_i|/\xi} R_j}{\sum_j e^{-2|\tau_j-\tau_i|/\xi}},
$$

where the sum is performed assuming periodic boundary conditions. If `noise_type = :Normal` then the random numbers of sampled according to $R_j \sim {\rm Normal}(0,\sigma)$. Otherwise,

$$
R_j \sim {\rm sign}(C(\tau_j)) \cdot P(|C(\tau_j)|, \sigma) - C(\tau_j)
$$

where $P(|C(\tau_j)|, \sigma)$ is either a Gamma or Truncated Normal distribution with mean and standard deviation given by $|C(\tau_j)|$ and $\sigma$ respectively.

The support for the Truncated Normal and Gamma distributions is $[0,\infty)$. Note that in the case that a Normal distribution is used it is possible for $C_{\rm noisy}(\tau_i)$ to have a different sign that $C(\tau_i)$, whereas this is not possible with the other two distributions.
