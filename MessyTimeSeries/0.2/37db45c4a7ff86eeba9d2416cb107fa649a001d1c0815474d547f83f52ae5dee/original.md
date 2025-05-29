```
DynamicKalmanStatus(...)
```

Define a mutable structure to handle any type of Kalman filter output.

The Kalman filter history is stored when `store_history` is set to true in the filter settings.

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
  * `history_X_prior`: History of a-priori X
  * `history_X_post`: History of a-posteriori X
  * `history_P_prior`: History of a-priori P
  * `history_P_post`: History of a-posteriori P
  * `history_e`: History of the forecast error
  * `history_inv_F`: History of the inverse of the forecast error covariance
  * `history_L`: History of the shortcut L
