```
qkf(model::QKModel{T,T2}, data::QKData{T1,N}) where {T1<:Real, T<:Real, T2<:Real, N}
```

Execute the full Quadratic Kalman Filter (QKF) process by combining both the filtering and backward smoothing stages. This function first applies the filtering routine to generate real-time state estimates and then refines these estimates using the smoother to incorporate information from future observations. The resulting output is a composite object that  encapsulates both the filtered and smoothed results.

Parameters:

  * model::QKModel{T,T2}: A model specification that includes the system dynamics, state transition parameters, and the augmented state representation. This object provides all necessary configurations to perform the QKF.
  * data::QKData{T1,N}: A data container comprising the observed time series measurements, formatted appropriately for the QKF. The parameter N indicates the dimension of the state vector, and T1 denotes the numerical type of the data.

Process:

1. Filtering Stage: The function invokes qkf_filter with the provided data and model to compute the filtered state estimates and error covariances.
2. Smoothing Stage: It then calls qkf_smoother to perform backward smoothing on the filtered results, enhancing the  state estimates by leveraging future information.

Returns:

  * QKFOutput{T}: A composite output object that bundles both filtering and smoothing results. This output includes:   • filter*output: The results from the filtering phase, containing state estimates and covariances.   • smoother*output: The refined state estimates obtained after applying the smoother.

This combined output is useful for subsequent analysis, diagnostics, and visualization of the QKF performance.
