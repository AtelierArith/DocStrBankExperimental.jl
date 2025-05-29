```
qkf_filter!(data::QKData{T1,1}, model::QKModel{T,T2})
```

Run the **Quadratic Kalman Filter (QKF)** on a time series of length `T̄`, modifying the result in-place.

# Description

This function implements a Kalman-like recursive filter where the state  vector `Zₜ` includes not only the usual mean component `xₜ` but also  terms for the second-moment `(x xᵀ)ₜ`, making it a *quadratic* extension.  At each time step, it performs:

1. **State Prediction** (`predict_Z_ttm1!` / `predict_P_ttm1!`)
2. **Measurement Prediction** (`predict_Y_ttm1!` / `predict_M_ttm1!`)
3. **Kalman Gain Computation** (`compute_K_t!`)
4. **State & Covariance Update** (`update_Z_tt!`, `update_P_tt!`)
5. **PSD Correction** (`correct_Z_tt!`)
6. **Log-Likelihood** computation for the current innovation.

Unlike the non-mutating version (`qkf_filter`), this function reuses  and mutates internal arrays and data structures in-place, which can  improve performance and reduce memory allocations.

# Arguments

  * `data::QKData{T1,1}`   A structure holding:

      * `Y::Vector{T1}` of length `T̄+1`, containing observations.  Typically, `Y[1]` is an initial placeholder and `Y[2..end]`  are the actual measurements.
      * `T_bar::Int` the total number of time steps (excluding index 0).
      * `M::Int` the dimension of the measurement at each time step.
  * `model::QKModel{T,T2}`   A parameter structure holding:

      * `N::Int`: State dimension (for the mean part).
      * `P::Int`: Dimension of the augmented "quadratic" state  (`P = N + N(N+1)/2`).
      * `μ_aug, Σ_aug`: The unconditional mean and covariance used for  initialization.
      * Additional model matrices or functions (e.g., `Φ_aug`, `B_aug`, `A`, `V`)  accessed via subroutines.

# Return

A named tuple with fields:

  * `ll_t::Vector{Float64}`   The per-time-step log-likelihoods (size = `T̄`).
  * `Z_tt::Array{T,3}`   The filtered state at each time step. Dimensions: `(T, P, T̄+1)` in your  specific code (or `(P, T̄+1)` in a more generic version).
  * `Pₜₜ::Array{T,4}`   The filtered state covariance array. Dimensions often `(T, P, P, T̄+1)`  in your code.
  * `Yₜₜ₋₁::Vector{T}`   The predicted measurement at each time step (size = `T̄`).
  * `M_ttm1::Array{T,4}`   The predicted measurement covariance, dimensions `(T, M, M, T̄)`.
  * `K_t::Array{T,4}`   The Kalman gain for each time step, `(T, P, M, T̄)`.
  * `Zₜₜ₋₁::Array{T,3}`   One-step-ahead predicted states.
  * `Pₜₜ₋₁::Array{T,4}`   One-step-ahead predicted covariances.
  * `Σ_ttm1::Array{T,4}`   Any intermediate covariance terms used for prediction.

# Details

1. **Initialization**: 

      * `Z_tt[:, 1] .= μ̃ᵘ` and `P_tt[:,:,1] .= Σ̃ᵘ`.
2. **Recursive Steps** (`for t in 1:T̄`):

      * **Prediction**: `predict_Z_ttm1!` / `predict_P_ttm1!`.
      * **Measurement**: `predict_Y_ttm1!` / `predict_M_ttm1!`.
      * **Gain & Update**: `compute_K_t!`, then `update_Z_tt!` / `update_P_tt!`.
      * **Correction**: `correct_Z_tt!` clamps negative eigenvalues  for PSD.
      * **Likelihood**: `compute_loglik!` appends the log-likelihood.
3. **Positive Semidefinite Correction**: 

      * Negative eigenvalues introduced by approximation are set to zero.

# Example

```julia
data = QKData(Y, M=measurement_dim, T̄=length(Y)-1)
model = QKModel(...)
result = qkf_filter!(data, model)

@show result.ll_t
@show result.Z_tt[:, end]   # final state
```
