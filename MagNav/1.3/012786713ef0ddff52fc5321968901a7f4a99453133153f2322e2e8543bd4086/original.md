```
ekf_online_nn(ins::INS, meas, itp_mapS, x_nn, m, y_norms, P0, Qd, R;
              baro_tau   = 3600.0,
              acc_tau    = 3600.0,
              gyro_tau   = 3600.0,
              fogm_tau   = 600.0,
              date       = get_years(2020,185),
              core::Bool = false)
```

Extended Kalman filter (EKF) with online learning of neural network weights.

**Arguments:**

  * `ins`:      `INS` inertial navigation system struct
  * `meas`:     scalar magnetometer measurement [nT]
  * `itp_mapS`: scalar map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
  * `x_nn`:     `N` x `Nf` data matrix for neural network (`Nf` is number of features)
  * `m`:        neural network model, does not work with skip connections
  * `y_norms`:  length-`2` tuple of `y` normalizations, `(y_bias,y_scale)`
  * `P0`:       initial covariance matrix
  * `Qd`:       discrete time process/system noise matrix
  * `R`:        measurement (white) noise variance
  * `baro_tau`: (optional) barometer time constant [s]
  * `acc_tau`:  (optional) accelerometer time constant [s]
  * `gyro_tau`: (optional) gyroscope time constant [s]
  * `fogm_tau`: (optional) FOGM catch-all time constant [s]
  * `date`:     (optional) measurement date (decimal year) for IGRF [yr]
  * `core`:     (optional) if true, include core magnetic field in measurement

**Returns:**

  * `filt_res`: `FILTres` filter results struct
