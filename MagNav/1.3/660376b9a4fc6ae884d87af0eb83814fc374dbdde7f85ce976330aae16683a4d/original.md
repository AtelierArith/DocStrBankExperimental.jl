```
ekf_online(ins::INS, meas, flux::MagV, itp_mapS, x0_TL, P0, Qd, R;
           baro_tau   = 3600.0,
           acc_tau    = 3600.0,
           gyro_tau   = 3600.0,
           fogm_tau   = 600.0,
           date       = get_years(2020,185),
           core::Bool = false,
           terms      = [:permanent,:induced,:eddy,:bias],
           Bt_scale   = 50000)
```

Extended Kalman filter (EKF) with online learning of Tolles-Lawson coefficients.

**Arguments:**

  * `ins`:      `INS` inertial navigation system struct
  * `meas`:     scalar magnetometer measurement [nT]
  * `flux`:     `MagV` vector magnetometer measurement struct
  * `itp_mapS`: scalar map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
  * `x0_TL`:    initial Tolles-Lawson coefficient states
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
  * `Bt_scale`: (optional) scaling factor for induced & eddy current terms [nT]

**Returns:**

  * `filt_res`: `FILTres` filter results struct
