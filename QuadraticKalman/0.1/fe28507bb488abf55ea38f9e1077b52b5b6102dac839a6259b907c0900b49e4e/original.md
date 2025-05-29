```
qkf_filter(data::QKData{T1,1}, model::QKModel{T,T2})
```

Run the **Quadratic Kalman Filter (QKF)** on a time series of length `T̄`,  returning a new set of result arrays (out-of-place).

# Description

This function implements the same *quadratic* Kalman filter recursion  as `qkf_filter!`, but instead of updating arrays in-place, it allocates  new arrays for predictions, updates, and outputs. This can be simpler to  use in contexts where you don't want to mutate or reuse `data` and `model`,  but it may be less memory-efficient for large-scale problems.

At each time step, it performs:

1. **State Prediction** (`predict_Z_tt` / `predict_P_tt`)
2. **Measurement Prediction** (`predict_Y_tt` / `predict_M_ttm1`)
3. **Kalman Gain Computation** (`compute_K_t`)
4. **State & Covariance Update** (`update_Z_tt`, `update_P_tt`)
5. **PSD Correction** (`correct_Zₜₜ`)
6. **Log-Likelihood** computation.

# Arguments

  * `data::QKData{T1,1}`   Same structure as in `qkf_filter!`, with fields:

      * `Y::Vector{T1}`, `T̄::Int`, `M::Int`.
  * `model::QKModel{T,T2}`   Same parameter structure as in `qkf_filter!`, with fields:

      * `N::Int`, `P::Int`, `μ̃ᵘ, Σ̃ᵘ`, etc.

# Return

A named tuple with fields:

  * `ll_t::Vector{Float64}`   Per-time-step log-likelihoods (size = `T̄`).
  * `Z_tt::Array{T,3}`   The filtered state at each time step (dimensions `(T, P, T̄+1)` in your usage).
  * `P_tt::Array{T,4}`   The filtered state covariance array.
  * `Y_ttm1::Vector{T}`   Predicted measurement for each step.
  * `M_ttm1::Array{T,4}`   Predicted measurement covariances.
  * `K_t::Array{T,4}`   The Kalman gain for each time step.
  * `Z_ttm1::Array{T,3}`   One-step-ahead predicted states.
  * `P_ttm1::Array{T,4}`   One-step-ahead predicted covariances.

# Details

1. **Initialization**:

      * Creates new arrays for `Z_tt` and `P_tt` and sets the initial state  to `aug_mean` and `aug_cov`.
2. **Time Loop**: 

      * **Prediction**: `predict_Z_tt`, `predict_P_tt`.
      * **Measurement**: `predict_Y_tt`, `predict_M_ttm1`.
      * **Gain & Update**: `compute_K_t`, `update_Z_tt`, `update_P_tt`.
      * **Correction**: `correct_Z_tt` for PSD.
      * **Likelihood**: `compute_loglik`.
3. **No In-Place Mutation**:

      * Each step returns fresh arrays; original inputs are not modified.

# Example

```julia
data = QKData(Y, M=measurement_dim, T̄=length(Y)-1)
model = QKModel(...)
result = qkf_filter(data, model)

@show result.ll_t
@show result.Z_tt[:, end]   # final state
```
