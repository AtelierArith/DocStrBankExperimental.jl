```
ekf_online_nn(lat, lon, alt, vn, ve, vd, fn, fe, fd, Cnb, meas,
              dt, itp_mapS, x_nn, m, y_norms, P0, Qd, R;
              baro_tau   = 3600.0,
              acc_tau    = 3600.0,
              gyro_tau   = 3600.0,
              fogm_tau   = 600.0,
              date       = get_years(2020,185),
              core::Bool = false,
              terms      = [:permanent,:induced,:eddy])
```

Extended Kalman filter (EKF) with online learning of neural network weights.

**Arguments:**

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
  * `dt`:       measurement time step [s]
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
  * `terms`:    (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}

**Returns:**

  * `filt_res`: `FILTres` filter results struct
