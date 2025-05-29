```
qkf_smoother!(filter_output::FilterOutput{T}, model::QKModel{T,T2}) where {T<:Real, T2<:Real}
```

Performs in-place backward smoothing for a Quadratic Kalman Filter (QKF) using the outputs obtained during filtering.

This function refines the filtered state estimates and covariance matrices by incorporating future observations, thereby producing a set of smoothed estimates. It operates by first extracting the filtered states (Z*tt) and their associated covariances (P*tt), as well as the one-step-ahead predictions (Z*ttm1 and P*ttm1) from the given FilterOutput structure. It then unpacks the augmented state parameters (H*aug, G*aug, Phi_aug) along with the state dimension (N) from the QKModel. The function makes local copies of the filtered estimates to avoid any modification of the original filtering results, and then calls the lower-level in-place smoothing routine to update these copies using the one-step-ahead predictions and the model parameters. The smoothed states and covariances are finally encapsulated into a SmootherOutput structure, which is returned.

Parameters:

  * filter*output: A FilterOutput instance containing:   • Z*tt    :: Matrix of filtered augmented state estimates for time steps 0 to T̄.   • P*tt    :: Array of filtered state covariance matrices.   • Z*ttm1  :: Matrix of one-step-ahead predicted augmented states.   • P_ttm1  :: Array of one-step-ahead predicted covariance matrices.
  * model: A QKModel instance providing the necessary model parameters for smoothing, including:   • aug*state: A structure containing:       - H*aug  :: The augmented measurement selection matrix.       - G*aug  :: The augmented duplication matrix for handling quadratic forms.       - Phi*aug:: The augmented state transition matrix.   • state: The dimension (N) of the state vector.

Returns:

  * A SmootherOutput structure containing:   • Z*smooth :: Matrix of smoothed augmented state estimates.   • P*smooth :: Array of smoothed state covariance matrices.
