```
ekf_online_setup(flux::MagV, meas, ind = trues(length(meas));
                 Bt           = sqrt.(flux.x.^2+flux.y.^2+flux.z.^2)[ind],
                 λ            = 0.025,
                 terms        = [:permanent,:induced,:eddy,:bias],
                 pass1        = 0.1,
                 pass2        = 0.9,
                 fs           = 10.0,
                 pole::Int    = 4,
                 trim::Int    = 20,
                 N_sigma::Int = 100,
                 Bt_scale     = 50000)
```

Setup for extended Kalman filter (EKF) with online learning of Tolles-Lawson coefficients.

**Arguments:**

  * `flux`:     `MagV` vector magnetometer measurement struct
  * `meas`:     scalar magnetometer measurement [nT]
  * `ind`:      selected data indices
  * `Bt`:       (optional) magnitude of vector magnetometer measurements or scalar magnetometer measurements for modified Tolles-Lawson [nT]
  * `λ`:        (optional) ridge parameter
  * `terms`:    (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `pass1`:    (optional) first passband frequency [Hz]
  * `pass2`:    (optional) second passband frequency [Hz]
  * `fs`:       (optional) sampling frequency [Hz]
  * `pole`:     (optional) number of poles for Butterworth filter
  * `trim`:     (optional) number of elements to trim after filtering
  * `N_sigma`:  (optional) number of Tolles-Lawson coefficient sets to use to create `TL_sigma`
  * `Bt_scale`: (optional) scaling factor for induced & eddy current terms [nT]

**Returns:**

  * `x0_TL`:    initial Tolles-Lawson coefficient states
  * `P0_TL`:    initial Tolles-Lawson covariance matrix
  * `TL_sigma`: Tolles-Lawson coefficients estimate std dev
