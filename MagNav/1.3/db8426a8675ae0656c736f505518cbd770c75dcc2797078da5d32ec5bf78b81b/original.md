```
mpf(lat, lon, alt, vn, ve, vd, fn, fe, fd, Cnb, meas, dt, itp_mapS;
    P0         = create_P0(),
    Qd         = create_Qd(),
    R          = 1.0,
    num_part   = 1000,
    thresh     = 0.8,
    baro_tau   = 3600.0,
    acc_tau    = 3600.0,
    gyro_tau   = 3600.0,
    fogm_tau   = 600.0,
    date       = get_years(2020,185),
    core::Bool = false)
```

Rao-Blackwellized (marginalized) particle filter (MPF) for airborne magnetic anomaly navigation. This simplified MPF works only with LINEAR dynamics. This allows the same Kalman filter covariance matrices to be used with each particle, simplifying the filter and reducing the computational load. It is especially suited for map-matching navigation in which there is a highly non-linear, non-Gaussian MEASUREMENT, but NOT non-linear dynamics. The filter also assumes NON-correlated measurements to speed up computation.

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
  * `P0`:       (optional) initial covariance matrix
  * `Qd`:       (optional) discrete time process/system noise matrix
  * `R`:        (optional) measurement (white) noise variance
  * `num_part`: (optional) number of particles
  * `thresh`:   (optional) resampling threshold fraction {0:1}
  * `baro_tau`: (optional) barometer time constant [s]
  * `acc_tau`:  (optional) accelerometer time constant [s]
  * `gyro_tau`: (optional) gyroscope time constant [s]
  * `fogm_tau`: (optional) FOGM catch-all time constant [s]
  * `date`:     (optional) measurement date (decimal year) for IGRF [yr]
  * `core`:     (optional) if true, include core magnetic field in measurement

**Returns:**

  * `filt_res`: `FILTres` filter results struct
