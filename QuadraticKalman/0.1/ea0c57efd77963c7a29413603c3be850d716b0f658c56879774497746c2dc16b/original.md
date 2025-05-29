```
params_to_model(params::Vector{T}, N::Int, M::Int) where T<:Real -> QKModel
```

Convert a parameter vector into a QKModel object with state and measurement parameters.

# Arguments

  * `params::Vector{T}`: A vector of unconstrained parameters.
  * `N::Int`: Dimension of the state vector.
  * `M::Int`: Dimension of the measurement vector.

# Returns

A `QKModel` object containing:

  * **State parameters:** (mu, Phi, Omega)   where the state equation is     Xₜ = μ + Φ Xₜ₋₁ + Omega εₜ. Here, Omega is constructed as Omega = D*state * D*state′, with D_state a lower–triangular matrix (of size N×N) whose diagonal entries are positive.
  * **Measurement parameters:** (A, B, C, D, α)   where the measurement equation is     Yₜ = A + B Xₜ + α Yₜ₋₁ + ∑₍ᵢ₌₁₎ᴹ Xₜ′ Cᵢ Xₜ + D εₜ. Here, D is constructed as D = D*meas * D*meas′, with D_meas a lower–triangular matrix (of size M×M) whose diagonal entries are positive.
  * Augmented state parameters and model moments (computed via helper functions).

# Parameter vector layout

The parameter vector is assumed to contain:

1. **State parameters:**

      * First `N` entries: state mean `mu`.
      * Next `N^2` entries: entries of `Phi` (stored columnwise).
      * Next `N(N+1)/2` entries: unconstrained parameters for D_state (used to form Omega).
2. **Measurement parameters:**

      * Next `M` entries: `A`.
      * Next `M×N` entries: entries of `B` (reshaped as an M×N matrix).
      * Next `M×N^2` entries: entries for `C`. (Interpreted as M matrices of size N×N.)
      * Next `M(M+1)/2` entries: unconstrained parameters for D_meas (used to form D).
      * Final `M×M` entries: entries of `α` (reshaped as an M×M matrix).

# Total expected length:

```
N + N^2 + N(N+1)/2  +  M + M×N + M×N^2 + M(M+1)/2 + M^2
```
