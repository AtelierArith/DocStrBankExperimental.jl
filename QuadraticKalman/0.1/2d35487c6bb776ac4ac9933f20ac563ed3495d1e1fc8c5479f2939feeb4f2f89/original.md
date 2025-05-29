```
QKFOutput{T<:Real}
```

Combined container for both filtering and smoothing outputs from the Quadratic Kalman algorithm.

This type encapsulates the results of the forward filtering pass—where state estimates and associated covariances are computed recursively based solely on past and present observations—and the subsequent backward smoothing pass that refines these estimates by incorporating future observations. The unified structure provides a clear and convenient interface for diagnostic analysis, visualization, and further model-based inference tasks.

# Fields

  * `filter::FilterOutput{T}`: Contains the outputs of the filtering process, such as the filtered log-likelihood, state estimates, and covariance matrices at each time step. These results represent the model’s estimates obtained in real time as the data was observed.
  * `smoother::SmootherOutput{T}`: Contains the outputs of the smoothing process, which refines and improves upon the filter results by leveraging information from the entire observation sequence. This typically includes the smoothed state estimates and corresponding covariance matrices, providing a more accurate reconstruction of the underlying state dynamics.

# Details

Using the QKFOutput structure, users can conveniently access both the instantaneous (filtering) and retrospectively improved (smoothing) estimates, making it easier to perform post-hoc analysis, diagnostics, or forecasting.
