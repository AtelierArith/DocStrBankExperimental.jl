```
qkf_filter!(data::QKData{T1,1}, model::QKModel{T,T2})
```

Run the **Quadratic Kalman Filter (QKF)** on a time series of length `T̄`.

# Description

This function implements a Kalman-like recursive filter where the state  vector `Z_t` includes not only the usual mean component `xₜ` but also  terms for the second-moment `(x xᵀ)ₜ`, making it a *quadratic* extension.  At each time step, it performs:

1. **State Prediction** (`predict_Z_ttm1` / `predict_P_ttm1`)
2. **Measurement Prediction** (`predict_Y_ttm1` / `predict_M_ttm1`)
3. **Kalman Gain Computation** (`compute_K_t`)
4. **State & Covariance Update** (`update_Zₜₜ!`, `update_Pₜₜ!`)
5. **PSD Correction**: Ensures the implied covariance is positive semidefinite  by clamping negative eigenvalues via `correct_Zₜₜ!`.
6. **Log-Likelihood** computation for the current innovation.

The filter stores and returns the entire history of filtered states, covariances, predicted measurements, and related arrays. 

# Arguments

  * `data::QKData{T1,1}`   A structure holding:

      * `Y::Vector{T1}` of length `T_bar+1`, which contains observations  (`Y[1]` is unused or some initial placeholder, and `Y[2..end]` are the actual measurements).
      * `T_bar::Int` the total number of time steps (excluding index 0).
      * `M::Int` the dimension of the measurement at each time step.
  * `model::QKModel{T,T2}`   A parameter structure holding:

      * `N::Int`: State dimension (for the mean part).
      * `P::Int`: Dimension of the augmented "quadratic" state vector  (`P = N + N(N+1)/2`).
      * `aug_mean, aug_cov`: The unconditional mean and covariance used for initialization.
      * Additional model matrices or functions (e.g., `Phi_aug`, `B_aug`, `A`, `V`),  typically accessed via separate predict/update subroutines.

# Return

A named tuple with fields:

  * `ll_t::Vector{Float64}`   The per-time-step log-likelihoods of the innovations (size = `T_bar`).
  * `Z_tt::Matrix{T}`   The updated ("filtered") state at each time step. Dimensions: `(P, T_bar+1)`,  where column `k` corresponds to time index `k-1`.
  * `P_tt::Array{T,3}`   The updated ("filtered") state covariance array (or the augmented second-moment  representation) at each time step. Dimensions: `(P, P, T_bar+1`.
  * `Y_ttm1::Vector{T}`   The predicted measurement at each time step (size = `T_bar`).
  * `M_ttm1::Array{T,3}`   The predicted measurement covariance at each time step (dimensions: `(M, M, T_bar)`).
  * `K_t::Array{T,3}`   The Kalman gain at each time step `(P, M, T_bar)`.
  * `Z_ttm1::Matrix{T}`   The one-step-ahead predicted state (dimensions: `(P, T_bar)`).
  * `P_ttm1::Array{T,4}`   The one-step-ahead predicted covariance (dimensions: `(P, P, T_bar)`).
  * `Σ_ttm1::Array{T,4}`   Any intermediate state-dependent covariance terms added during prediction  (dimensions: `(P, P, T_bar)`).

# Details

1. **Initialization**:  

      * `Z_tt[:,1] .= aug_mean` and `P_tt[:,:,1] .= aug_cov`, representing the state at time 0.
2. **Time Loop** (`for t in 1:T_bar`):  

      * **Predict** step: 

          * `predict_Z_ttm1` sets `Z_ttm1[:,t]` from `Z_tt[:,t]`.
          * `predict_P_ttm1` sets `P_ttm1[:,:,t]` from `P_tt[:,:,t]`.
      * **Measurement** step: 

          * `predict_Y_ttm1` computes `Y_ttm1[t]` from `Z_ttm1[:,t]`.
          * `predict_M_ttm1` updates `M_ttm1[:,:,t]`.
      * **Gain & Update**:

          * `compute_K_t` obtains the Kalman gain `K_t[:,:,t]`.
          * `update_Z_tt` and `update_P_tt` yield the next `Z_tt[:,t+1]` and `P_tt[:,:,t+1]`.
      * **Correction**:  

          * `correct_Z_tt` clamps negative eigenvalues in the implied covariance portion  of `Z_tt` to ensure PSD.
      * **Likelihood**:

          * `compute_loglik` appends/logs the innovation-based log-likelihood  in `ll_t[t]`.
3. **Positive Semidefinite Correction**:

      * Because the filter tracks `[X Xᵀ] - X Xᵀᵀ` as a covariance block, it can  become indefinite due to linearization or numerical issues. We enforce  PSD by zeroing out negative eigenvalues in `correct_Z_tt`.
      * This step is not strictly differentiable at eigenvalues crossing zero.  If you need AD through the filter, consider an alternative correction  or a custom adjoint.

# Example

```julia data = QKData(Y, M=measurement*dim, T*bar=length(Y)-1) model = QKModel( ... )   # set up your model

result = qkf_filter!(data, model)

@show result.ll*t @show result.Z*tt[:, end]   # final state vector
