```
ekf(ins::INS, meas, itp_mapS;
    P0         = create_P0(),
    Qd         = create_Qd(),
    R          = 1.0,
    baro_tau   = 3600.0,
    acc_tau    = 3600.0,
    gyro_tau   = 3600.0,
    fogm_tau   = 600.0,
    date       = get_years(2020,185),
    core::Bool = false,
    der_mapS   = map_itp(zeros(2,2),[-pi,pi],[-pi/2,pi/2]),
    map_alt    = 0)
```

Extended Kalman filter (EKF) for airborne magnetic anomaly navigation.

**Arguments:**

  * `ins`:      `INS` inertial navigation system struct
  * `meas`:     scalar magnetometer measurement [nT]
  * `itp_mapS`: scalar map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
  * `P0`:       (optional) initial covariance matrix
  * `Qd`:       (optional) discrete time process/system noise matrix
  * `R`:        (optional) measurement (white) noise variance
  * `baro_tau`: (optional) barometer time constant [s]
  * `acc_tau`:  (optional) accelerometer time constant [s]
  * `gyro_tau`: (optional) gyroscope time constant [s]
  * `fogm_tau`: (optional) FOGM catch-all time constant [s]
  * `date`:     (optional) measurement date (decimal year) for IGRF [yr]
  * `core`:     (optional) if true, include core magnetic field in measurement
  * `der_mapS`: (optional) scalar map vertical derivative map interpolation function (`f(lat,lon)` or (`f(lat,lon,alt)`)
  * `map_alt`:  (optional) map altitude [m]

**Returns:**

  * `filt_res`: `FILTres` filter results struct
