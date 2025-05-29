```
(ekf_rt::EKF_RT)(ins::INS, meas, itp_mapS;
                 der_mapS = nothing,
                 map_alt  = -1)
```

Real-time (RT) extended Kalman filter (EKF) for airborne magnetic anomaly navigation. Receives individual samples and updates time, covariance matrix, state vector, and measurement residual within `ekf_rt` struct.

**Arguments:**

  * `ekf_rt`:   `EKF_RT` real-time extended Kalman filter struct
  * `ins`:      `INS` inertial navigation system struct with individual sample (`ins.N=1`)
  * `meas`:     scalar magnetometer measurement [nT]
  * `itp_mapS`: scalar map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
  * `der_mapS`: (optional) scalar map vertical derivative map interpolation function (`f(lat,lon)` or (`f(lat,lon,alt)`)
  * `map_alt`:  (optional) map altitude [m]

**Returns:**

  * `filt_res`: `FILTres` filter results struct,
  * `ekf_rt`:   `t`, `P`, `x`, & `r` fields are mutated
