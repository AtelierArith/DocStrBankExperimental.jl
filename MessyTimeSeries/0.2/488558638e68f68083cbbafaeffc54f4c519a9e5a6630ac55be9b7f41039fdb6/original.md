```
SizedKalmanStatus(...)
```

Define an immutable structure that always store the filter history up to time $T$.

# Arguments

  * `online_status`: `OnlineKalmanStatus` struct
  * `history_length`: History length
  * `history_X_prior`: History of a-priori X
  * `history_X_post`: History of a-posteriori X
  * `history_P_prior`: History of a-priori P
  * `history_P_post`: History of a-posteriori P
  * `history_e`: History of the forecast error
  * `history_inv_F`: History of the inverse of the forecast error covariance
  * `history_L`: History of the shortcut L
