```
(ekf_rt::EKF_RT)(lat, lon, alt, vn, ve, vd, fn, fe, fd,
                 Cnb, meas, t, itp_mapS;
                 der_mapS = nothing,
                 map_alt  = -1,
                 dt       = 0.1)
```

Real-time (RT) extended Kalman filter (EKF) for airborne magnetic anomaly navigation. Receives individual samples and updates time, covariance matrix, state vector, and measurement residual within `ekf_rt` struct.

**Arguments:**

  * `ekf_rt`:   `EKF_RT` real-time extended Kalman filter struct
  * `lat`:      latitude  [rad]
  * `lon`:      longitude [rad]
  * `alt`:      altitude  [m]
  * `vn`:       north velocity [m/s]
  * `ve`:       east  velocity [m/s]
  * `vd`:       down  velocity [m/s]
  * `fn`:       north specific force [m/s^2]
  * `fe`:       east  specific force [m/s^2]
  * `fd`:       down  specific force [m/s^2]
  * `Cnb`:      direction cosine matrix (body to navigation) [-]
  * `meas`:     scalar magnetometer measurement [nT]
  * `t`:        time [s]
  * `itp_mapS`: scalar map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
  * `der_mapS`: (optional) scalar map vertical derivative map interpolation function (`f(lat,lon)` or (`f(lat,lon,alt)`)
  * `map_alt`:  (optional) map altitude [m]
  * `dt`:       (optional) measurement time step [s], only used if `ekf_rt.t < 0`

**Returns:**

  * `filt_res`: `FILTres` filter results struct,
  * `ekf_rt`:   `t`, `P`, `x`, & `r` fields are mutated
