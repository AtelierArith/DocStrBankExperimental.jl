```
OnlineKalmanStatus(...)
```

Define a mutable structure to handle minimal Kalman filter output. 

The Kalman filter history is not stored. This makes it ideal for online filtering problems. However, it is incompatible with the kalman smoother implementation.

# Arguments

  * `t`: Current point in time
  * `loglik`: Loglikelihood
  * `X_prior`: Latest a-priori X
  * `X_post`: Latest a-posteriori X
  * `P_prior`: Latest a-priori P
  * `P_post`: Latest a-posteriori P
  * `e`: Forecast error
  * `inv_F`: Inverse of the forecast error covariance
  * `L`: Convenient shortcut for the filter and smoother
  * `buffer_J1`, `buffer_J2`, `buffer_m_m`, `buffer_m_n_obs`: Buffer arrays used for low-level matrix operations
