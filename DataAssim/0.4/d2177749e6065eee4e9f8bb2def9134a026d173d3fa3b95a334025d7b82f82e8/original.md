```
x,P = KalmanFilter(xi,Pi,ℳ,Q,yo,R,𝓗,nmax,no)
```

Kalman Filter with the model `ℳ` and `nmax` time-steps starting at the initial condition `xi` and error covariance `Pi`. Observations `yo` (and error covariance `R`) at the time steps given in `no` are assimilated with the observation operator `H`.
