```
run_filt(traj::Traj, ins::INS, meas, itp_mapS, filt_type::Symbol = :ekf;
         P0             = create_P0(),
         Qd             = create_Qd(),
         R              = 1.0,
         num_part       = 1000,
         thresh         = 0.8,
         baro_tau       = 3600.0,
         acc_tau        = 3600.0,
         gyro_tau       = 3600.0,
         fogm_tau       = 600.0,
         date           = get_years(2020,185),
         core::Bool     = false,
         map_alt        = 0,
         x_nn           = nothing,
         m              = nothing,
         y_norms        = nothing,
         terms          = [:permanent,:induced,:eddy,:bias],
         flux::MagV     = MagV([0.0],[0.0],[0.0],[0.0]),
         x0_TL          = ones(eltype(P0),19),
         extract::Bool  = true,
         run_crlb::Bool = true)
```

Run navigation filter and optionally compute Cramér–Rao lower bound (CRLB).

**Arguments:**

  * `traj`:      `Traj` trajectory struct
  * `ins`:       `INS` inertial navigation system struct
  * `meas`:      scalar magnetometer measurement [nT]
  * `itp_mapS`:  scalar map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
  * `filt_type`: (optional) filter type {`:ekf`,`:mpf`}
  * `P0`:        (optional) initial covariance matrix
  * `Qd`:        (optional) discrete time process/system noise matrix
  * `R`:         (optional) measurement (white) noise variance
  * `num_part`:  (optional) number of particles, only used for `filt_type = :mpf`
  * `thresh`:    (optional) resampling threshold fraction {0:1}, only used for `filt_type = :mpf`
  * `baro_tau`:  (optional) barometer time constant [s]
  * `acc_tau`:   (optional) accelerometer time constant [s]
  * `gyro_tau`:  (optional) gyroscope time constant [s]
  * `fogm_tau`:  (optional) FOGM catch-all time constant [s]
  * `date`:      (optional) measurement date (decimal year) for IGRF [yr]
  * `core`:      (optional) if true, include core magnetic field in measurement
  * `map_alt`:   (optional) map altitude [m]
  * `x_nn`:      (optional) `N` x `Nf` data matrix for neural network (`Nf` is number of features)
  * `m`:         (optional) neural network model
  * `y_norms`:   (optional) tuple of `y` normalizations, i.e., `(y_bias,y_scale)`
  * `terms`:     (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `flux`:      (optional) `MagV` vector magnetometer measurement struct
  * `x0_TL`:     (optional) initial Tolles-Lawson coefficient states
  * `extract`:   (optional) if true, extract output structs
  * `run_crlb`:  (optional) if true, compute the Cramér–Rao lower bound (CRLB)

**Returns:**

  * if `extract = true`  & `run_crlb = true`

      * `crlb_out`: `CRLBout` Cramér–Rao lower bound extracted output struct
      * `ins_out`:  `INSout`  inertial navigation system extracted output struct
      * `filt_out`: `FILTout` filter extracted output struct
  * if `extract = true`  & `run_crlb = false`

      * `filt_out`: `FILTout` filter extracted output struct
  * if `extract = false` & `run_crlb = true`

      * `filt_res`: `FILTres` filter results struct
      * `crlb_P`:   Cramér–Rao lower bound non-linear covariance matrix
  * if `extract = false` & `run_crlb = false`

      * `filt_res`: `FILTres` filter results struct
