```
qkf_smoother(filter_output::FilterOutput{T}, model::QKModel{T,T2}) where {T<:Real, T2<:Real}
```

Performs out-of-place backward smoothing for the Quadratic Kalman Filter (QKF) using filtering outputs. This function refines the state estimates produced during filtering by incorporating future observations through a backward smoothing pass.

# Arguments

  * filter*output::FilterOutput{T}: A container holding the outputs from the filtering phase, including:   • Z*tt: A matrix of filtered augmented state estimates.   • P*tt: An array of filtered state covariances.   • Z*ttm1: A matrix containing the one-step-ahead predicted states.   • P_ttm1: An array containing the one-step-ahead predicted state covariances.
  * model::QKModel{T,T2}: A model specification that provides the necessary parameters for the smoothing process. The model includes an `aug_state` field which is unpacked to retrieve:   • H*aug: The augmented measurement selection matrix.   • G*aug: The augmented duplication matrix used for handling quadratic forms.   • Phi_aug: The augmented state transition matrix. Additionally, the `state` field is used to extract the dimensionality (N) of the state.

# Details

This function first creates copies of the filtered state and covariance estimates to prevent modification of the original filtering outputs. It then invokes the in-place smoother routine (`qkf_smoother!`) on these copies using the one-step-ahead predicted values and the model's parameters. The final smoothed results are wrapped in a `SmootherOutput` struct and returned as fresh copies, which is particularly important for compatibility with automatic differentiation (AD) workflows.

# Returns

  * SmootherOutput: A composite structure containing:   • Z*smooth: A matrix of smoothed augmented state estimates.   • P*smooth: An array of smoothed state covariance matrices.
