```
crlb(traj::Traj, itp_mapS;
     P0         = create_P0(),
     Qd         = create_Qd(),
     R          = 1.0,
     baro_tau   = 3600.0,
     acc_tau    = 3600.0,
     gyro_tau   = 3600.0,
     fogm_tau   = 600.0,
     date       = get_years(2020,185),
     core::Bool = false)
```

Cramér–Rao lower bound (CRLB) computed with classic Kalman Filter. Equations evaluated about true trajectory.

**Arguments:**

  * `traj`:     `Traj` trajectory struct
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

**Returns:**

  * `P`: non-linear covariance matrix
