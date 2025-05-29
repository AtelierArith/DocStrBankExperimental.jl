```
qkf_smoother!(
    Z::AbstractMatrix{T},      # Filtered states   (P × (T_bar+1))
    P::AbstractArray{T, 3},    # Filtered covariances (P × P × (T_bar+1))
    Z_pred::AbstractMatrix{T}, # One-step-ahead predicted states (P × T_bar)
    P_pred::AbstractArray{T,3},
    T_bar::Int,
    Hn::Matrix{T},  Gn::Matrix{T},  H_aug::Matrix{T},  Φ_aug::Matrix{T},
    dof::Int
) where {T<:Real}
```

Perform **in-place** backward smoothing for the Quadratic Kalman Filter (QKF).

# Description

Given the forward-filtered estimates `(Z, P)` from `t=1..T_bar`, plus the  one-step-ahead predictions `(Z_pred, P_pred)` and the special matrices  (H*aug, G*aug) that handle the dimension reduction via  Vech(·)/Vec(·), this function computes `Z[:,t]` and `P[:,:,t]` for  `t = T_bar-1 .. 1` in backward fashion to produce the smoothed estimates  (Zₜ|T*bar, PZₜ|T*bar).  

## Mathematical Form (Backward Pass)

1. Compute   Fₜ = (H̃ₙPᵗ|ᵗᶻH̃ₙ')(H̃ₙΦ̃G̃ₙ)'(H̃ₙPᵗ⁺¹|ᵗᶻH̃ₙ')⁻¹ but implemented via solves (rather than explicit inverses) for numerical stability.
2. Then update (in H̃ₙ-transformed space): H̃ₙZₜ|ₜ = H̃ₙZₜ|ₜ + Fₜ(H̃ₙZₜ₊₁|ₜ - H̃ₙZₜ₊₁|ₜ)
3. And similarly for the covariance: (H̃ₙPᵗ|ᵀᶻH̃ₙ') = (H̃ₙPᵗ|ᵗᶻH̃ₙ') + Fₜ[(H̃ₙPᵗ⁺¹|ᵀᶻH̃ₙ') - (H̃ₙPᵗ⁺¹|ᵗᶻH̃ₙ')]Fₜ'
4. Finally, transform back to get `Zₜ|T` and `Pᵗ|ᵀᶻ` in the full (Vec/augmented) space if necessary.

# Arguments

  * `Z::AbstractMatrix{T}`: On entry, `Z[:,t]` = `Zₜ|T` for each `t`. On exit, it will contain the smoothed states `Zₜ|T`.
  * `P::AbstractArray{T,3}`: On entry, `P[:,:,t]` = `Pᵗ|ᵀᶻ`.  On exit, `P[:,:,t]` = `Pᵗ|ᵀᶻ`.
  * `Z_pred::AbstractMatrix{T}`, `P_pred::AbstractArray{T,3}`:  The one-step-ahead predicted states/covariances from the forward pass, i.e. `Z_pred[:,t] = Zₜ|ₜ`, `P_pred[:,:,t] = P^Zₜ|ₜ`.
  * `T_bar::Int`: Total time steps (excluding time 0).
  * `Hn::Matrix{T}`, `Gn::Matrix{T}`: The selection/duplication operators  for Vec/Vech transforms of block `(x xᵀ)`. Usually size `(n(n+1) × n(n+3)/2)` or similarly.
  * `H_aug::Matrix{T}`, `Φ_aug::Matrix{T}`: The augmented versions  (H*aug, G*aug) used in the QKF recursion.
  * `dof::Int`: Dimension parameter (often `n` or `P`). Adjust to your model.

# Notes

  * This function runs backward from `t = T_bar-1` down to `t = 1`, using  the final values `(Z[:, T_bar], P[:,:, T_bar])` as the terminal condition  (`Z_{T_bar|T_bar}, P^Z_{T_bar|T_bar}`).
  * If your AD library supports destructive updates, this approach should  be AD-friendly; if not, consider the out-of-place version `qkf_smoother`.

# Example

Suppose you already ran the forward filter, so you have:     Z, P, Z*pred, P*pred, plus your special matrices.

```
qkf_smoother!(Z, P, Z_pred, P_pred, T_bar, Hn, Gn, H_aug, Φ_aug, n)
```
