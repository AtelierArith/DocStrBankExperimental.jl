```
FilterOutput{T<:Real}
```

A container for the outputs produced by the Quadratic Kalman Filter applied to state-space models with quadratic measurement equations. This structure organizes and stores all key filtering results, facilitating subsequent analysis, diagnostics, or visualization. 

Fields:   • ll*t::Vector{T}        A vector containing the log-likelihood values computed at each time step.   • Z*tt::Matrix{T}        A matrix representing the filtered state estimates at the current time step.   • P*tt::Array{T,3}        A 3-dimensional array containing the error covariance matrices corresponding to the filtered state estimates.   • Y*ttm1::Union{Vector{T}, Matrix{T}}       The one-step-ahead (t-1) predicted measurements; it can be a vector for univariate cases or a matrix for multivariate cases.   • M*ttm1::Array{T,3}        A 3-dimensional array holding auxiliary statistics from the filtering process.   • K*t::Array{T,3}        A 3-dimensional array of Kalman gain matrices computed at each filter update.   • Z*ttm1::Matrix{T}        A matrix of the one-step-ahead state predictions (prior estimates).   • P*ttm1::Array{T,3}        A 3-dimensional array representing the error covariance matrices for the one-step-ahead state predictions.

Usage:     This structure is used to encapsulate all relevant outputs from the Quadratic Kalman Filter, ensuring that users can easily access and work with the filtered estimates, prediction errors, and associated metrics that describe the performance of the filtering process.
