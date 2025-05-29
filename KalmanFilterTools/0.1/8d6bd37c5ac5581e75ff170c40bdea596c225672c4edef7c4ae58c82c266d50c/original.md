Module KalmanFilterTools provides algorithms for computing the Kalman filter, the Kalman smoother and the log-likelihood of a state space model using the Kalman filter.

The state space is given by

```
    y_t = Z_t α_t + ϵ_t
    α_{t+1} = T α_t + Rη_t
```
