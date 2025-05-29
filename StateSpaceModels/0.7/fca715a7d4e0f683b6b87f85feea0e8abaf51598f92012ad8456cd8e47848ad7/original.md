```
FilterOutput{Fl<:Real}
```

Structure with the results of the Kalman filter:

  * `v`: innovations
  * `F`: variance of innovations
  * `a`: predictive state
  * `att`: filtered state
  * `P`: variance of predictive state
  * `Ptt`: variance of filtered state
  * `Pinf`: diffuse part of the covariance
