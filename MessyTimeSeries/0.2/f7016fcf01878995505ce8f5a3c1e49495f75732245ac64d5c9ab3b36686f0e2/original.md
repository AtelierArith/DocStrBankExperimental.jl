```
ksmoother(settings::KalmanSettings, status::KalmanStatus, t_stop::Int64=1)
```

Kalman smoother: RTS smoother from the last evaluated time period in `status` up to $t==0$.

The smoother is implemented following the approach proposed in Durbin and Koopman (2012).

# Arguments

  * `settings`: KalmanSettings struct
  * `status`: KalmanStatus struct
  * `t_stop`: Optional argument that can be used to define the last smoothing period (default: 1)
